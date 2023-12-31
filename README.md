# The instruction is not finished yet. Please use the official documentation

**The OpenMetaData repository does not allow downloading the docker container for the RU Internet**

https://docs.open-metadata.org/v1.2.x/quick-start/local-docker-deployment

# Installing OpenMetadata with docker-compose.

## Quick Installation

**Before starting the instance, direct the domain (subdomain) to the ip of the server where OpenMetadata will be installed!**

## 1. OpenMetadata Server Requirements
From and more
- 2 CPUs
- 4 RAM 
- 10 Gb 

Run for Ubuntu 22.04

``` bash
sudo apt-get purge needrestart
```

## 2.Install docker and docker-compose:

``` bash
curl -s https://raw.githubusercontent.com/6Ministers/penpot-docker-compose-for-prototypes-apps/master/setup.sh | sudo bash -s
```

If `curl` is not found, install it:

``` bash
$ sudo apt-get install curl
# or
$ sudo yum install curl
```


## Procedure
1. Create a directory for OpenMetadata
Create a new directory for OpenMetadata and navigate into that directory.

``` bash
mkdir openmetadata-docker && cd openmetadata-docker
```

2. Download Docker Compose File from GitHub Releases
Download the docker-compose.yml file from the release page here.

The latest version is at the top of the page

Deploying with MySQL: Download docker-compose.yml file from the above link.
Deploying with PostgreSQL: Download docker-compose-postgres.yml file from the above link.
You can use the curl or wget command as well to fetch the docker compose files from your terminal -

``` bash
curl -sL -o docker-compose.yml https://github.com/open-metadata/OpenMetadata/releases/download/1.2.2-release/docker-compose.yml

curl -sL -o docker-compose-postgres.yml https://github.com/open-metadata/OpenMetadata/releases/download/1.2.2-release/docker-compose-postgres.yml
```

3. Start the Docker Compose Services
Run the below command to deploy the OpenMetadata

For OpenMetadata with MySQL Database -
``` bash
docker compose -f docker-compose.yml up --detach
```

For OpenMetadata with PostgreSQL Database -
``` bash
docker compose -f docker-compose-postgres.yml up --detach
```


Log in to OpenMetadata
OpenMetadata provides a default admin account to login.

You can access OpenMetadata at http://localhost:8585. Use the following credentials to log in to OpenMetadata.

Username: admin
Password: admin
Once you log in, you can goto Settings -> Users to add another user and make them admin as well.

Log in to Airflow
OpenMetadata ships with an Airflow container to run the ingestion workflows that have been deployed via the UI.

In the Airflow, you will also see some sample DAGs that will ingest sample data and serve as an example.

You can access Airflow at http://localhost:8080. Use the following credentials to log in to Airflow.

Username: admin
Password: admin

Documents:

https://docs.open-metadata.org/v1.2.x/quick-start/local-docker-deployment
