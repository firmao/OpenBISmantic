
# openBISmantic [![Publish Docker image](https://github.com/Mat-O-Lab/OpenBISmantic/actions/workflows/PublishContainer.yml/badge.svg)](https://github.com/Mat-O-Lab/OpenBISmantic/actions/workflows/PublishContainer.yml) ![Export Data](https://github.com/Mat-O-Lab/OpenBISmantic/actions/workflows/ExportData.yml/badge.svg)
Demonstrator of a Export Mechanism for openBIS Data to Semantic Data.

# Prototype
```bash
URL: https://openbismantic.matolab.org/openbis/webapp/eln-lims
user: public-user
password: public
after login access the URL: https://openbismantic.matolab.org/openbismantic
```
![image](https://github.com/Mat-O-Lab/OpenBISmantic/assets/9248325/a88e19f3-00c5-4817-83c4-ed3f5cb9ce3b)
```bash
Click in "exporter"
Select some instance and click on the button "Load selected"
Then you can export the triples in .ttl format or run a SPARQL query.
```

# Install

## pull repository
```bash
git clone https://github.com/Mat-O-Lab/OpenBISmantic.git
cd OpenBISmantic
```
## create a .env file with
```bash

ADMIN_PASS=<adminpassw>
HOST_NAME=<fqurlofhost> (e.g., openbis.matolab.org)
OPENBIS_PORT=<port> (e.g., 80)
OPENBIS_SSL_PORT=<port> (e.g., 443)
POSTGRES_PASSWORD=<postgrespassw>
GROUP_NAME=<groupname> (e.g., matolab)
GROUP_ID=<gid> (e.g., 12940)
```
## pull plugin submodule
To clone the submodule:
```bash
cd OpenBISmantic-plugin
git submodule update --init --recursive
cd ..
```

## run server
```bash
docker compose up -d
```

## stop server and clean up
```bash
docker compose down
docker system prune --all
```

# Notes

## data retention
The current configuration is intended to **not** support data retention. If required, please add to `docker-compose.yml` the following lines:
```
    openbis:
        ...
        volumes:
        - openbis_vol:/home/openbis/openbis_state
    
volumes:
    openbis_vol:
        name: openbis_vol

```
