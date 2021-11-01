# Kibana + Elasticsearch

This project lets you install **Elasticsearch** database and **Kibana** dashboard using docker service.

## Prerequisites

Make sure you have installed these:
- [Docker and Docker Compose](https://phoenixnap.com/kb/install-docker-compose-on-ubuntu-20-04) - Will install all the required packages and software.


## Installation

Make a copy of `.env.example` file named `.env`

```shell script
cp .env.example .env
```

---

Environment variables:
- **Kibana and Elasticsearch settings** settings:
    - `IMAGE_TAG` - **Elasticsearch** and **Kibana** image tag
    - `ES_PORT` - exposed port for **Elasticsearch**
    - `CLUSTER_PORT` - custom binary protocol used for communications between nodes in a cluster.
    - `KIBANA_PORT` - port, on which **Kibana** instance will be running.
    - `ELASTIC_PASSWORD` - password for **Kibana** dashboard interface for default user *elastic*.
- `DATABASE_NETWORK` - network, on which our database will be accessible.

```dotenv
# Kibana and Elasticsearch settings
IMAGE_TAG=7.14.2
ES_PORT=9200
CLUSTER_PORT=9300
KIBANA_PORT=5601
ELASTIC_PASSWORD=password

# Network settings
DATABASE_NETWORK=database_network

```

---

Create network with the name, that we have in `DATABASE_NETWORK` environment variable.

```shell script
docker network create database_network
```

---

Build the Docker image

```shell script
docker-compose build
```

## Running

Start
```
docker-compose up
```

Stop
```
docker-compose down
```

## Usage

- Access **Kibana** interface instance through  `localhost:KIBANA_PORT` from browser.
