# compose-homelab
Everything needed for a turnkey developer + devops + self-hosted system. Easily stand up your own development, self hosted, and DevOps oriented stack. 

## To Get Started (Quick)
* Suggested system components: 
  * RAM: 24GB
  * CPU: 4 Core (Virtualization enabled)
  * If on HyperVisor: Cache Writethrough & VT-d enabled
* You will need [docker](https://docs.docker.com/get-docker/) and [docker-compose](https://docs.docker.com/compose/install/) installed on your system
* You will need to portforward `80` & `443` for things to work as expected on your router
* duckdns? Cloudflare?
* In the root of this repository's directory, run `docker-compose up -d`
* Sit back and watch your computer computate

## Description
Easily stand up your own development, self hosted, and DevOps oriented stack. 
Some of the systems used(OBVIOUSLY not serves I have anything to do with, I seek no credit of the following services, google them for more research):
### DevOps:
  * GitLab
  * TeamCity
  * Artifactory
  * Grafana
  * Loki
  * Promtail
  * InfluxDB
  * Prometheus
  * AlertManager
  * AWX
  * Guacamole
  * Zabbix
### Development:
  * VSCode (server)
  * Jupyter Notebook
  * MongoDB
  * Postgres
  * MySQL
  * Neo4J
### Hosting:
  * Traefik
  * Springboot backend (custom java project)
  * Tornado (Custom python project)
  * WordPress (needs to be added yet)
  * Drupal
### Documentation:
* YouTrack
* Netbox
* Whiteboard
* NextCloud
### Misc:
* Plex

## To Get Started
* You will need docker and docker compose installed on your system
* You will need to port-forward ports `80` and `443` for things to work as expected
* In the root of this repository's directory, run `docker-compose up -d`
* Sit back and watch your computer computate

## To Customize: 
* If you know what you want, you'll know to comment out services you don't want to start up, customize the ports they run on, or specify which services you want to start, such as `docker-compose up -d traefik teamcity-server teamcity-agent gitlab`

## Contribute?
There are so many undiscovered services, of which could make great alternatives
### TO DO: