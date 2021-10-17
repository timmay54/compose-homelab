# compose-homelab
Everything needed for a turnkey developer+devops+self-hosted system. Easily stand up your own development, self hosted, and DevOps oriented stack. 

## To Get Started (Quick)
* Suggested system components: 
  * RAM: 24GB
  * CPU: 4 Core (Virtualization enabled)
  * If on HyperVisor: Cache Writethrough & VT-d enabled
* You will need [docker](https://docs.docker.com/get-docker/) and [docker-compose](https://docs.docker.com/compose/install/) installed on your system
* You will need to portforward `80` & `443` for things to work as expected on your router
* duckdns?
* In the root of this repository's directory, run `docker-compose up -d`
* Sit back and watch your computer computate

## Description
Some of the systems used (OBVIOUSLY I have nothing to do with the services that are about to be listed, I seek no credit of the following services, google them for more research, I am not paid by any of these companies, use at your own risk, etc...):
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
### Development:
  * VSCode (server)
  * Jupyter Notebook
  * MongoDB
  * Postgres
  * MariaDB
  * MySQL
  * Neo4J
### Hosting:
  * Traefik
  * Springboot backend (custom java project)
  * Tornado (Custom python project)
  * WordPress (needs to be added yet)

Leveraging Traefik is most of the magic behind the scenes. With my DD-WRT router port forwarding a few ports, I am even able to open up some services that control my thermostat and garage door remotely. 

## Get Started (Long version): 
* If you know what you want, you'll know to comment out services you don't want to start up, customize the ports they run on, or specify which services you want to start, such as `docker-compose up -d traefik teamcity-server teamcity-agent gitlab`
* Create subfolders for each service, each subfolder will need different sub-subfolders according to the container image's needs. 
* Understand that some services use these subfolders/volumes for longterm storage, and others use 

## Contribute?
There are so many undiscovered services, of which could make great alternatives

## TO DO:
* Scripts:
  * Set up folder heiarchy
  * Something like JHipster init script, allowing users to change out service for other brands
  * script for auto replacement of strings in files (email for LE, ip of server, url of dynamic dns, variable replacement, etc)
* Services to add/fix:
  * Jfrog
  * Artifactory
  * Alerta 
  * PiHole
  * Authelia
  * Morgue
  * GitLab (works, but not with Traefik external access)
  * ChatOps service?
  * WatchTower (a service that is supposed to update services?)
  * More web content hosting sites (Plex, WordPress, Drupal, ETC)
* Configurations to update:
  * Traefik needs updated (I had very similar setup working on 2.3.7, but now does not work)
  * AlertManager needs fine tuning for each service
  * Telegraf configuration should be added
  * Prometheus rules to be added
  * InfluxDB configuration
* MISCELLANIOUS WORK:
  * GH Action to test standing up all services?
  * Add more environment variables to all services
  * add documentation for Loki Driver, best piece of logging of all time
  * documentation for quick setup and then for more entracate setup