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

## Quick Start: 
1. `git clone https://github.com/timmay54/compose-homelab.git`
2. `cd compose-homelab`
3. `mv example.env .env`
4. `docker-compose up -d`

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
* Kafka
* NodeRed
* Splunk
* Vault
* AWX
* Guacamole
* Zabbix
### Development:
* VSCode (server)
* Jupyter Notebook
* MongoDB
* Postgres
* MariaDB
* MySQL
* Neo4J
* Redis
### Documentation:
* YouTrack
* Netbox
* Whiteboard
* NextCloud
### Misc:
* Plex
### Hosting:
* Traefik
* Springboot backend (custom java project)
* Tornado (Custom python project)
* WordPress (needs to be added yet)
* Drupal

Leveraging Traefik is most of the magic behind the scenes. With my DD-WRT router port forwarding a few ports, I am even able to open up some services that control my thermostat and garage door remotely. 

## Get Started (Long version): 
* If you know what you want, you'll know to comment out services you don't want to start up, customize the ports they run on, or specify which services you want to start, such as `docker-compose up -d traefik teamcity-server teamcity-agent gitlab`
* Create subfolders for each service, each subfolder will need different sub-subfolders according to the container image's needs. 
* Understand that some services use these subfolders/volumes for longterm storage, and others use 

## Contribute?
There are so many undiscovered services, of which could make great alternatives

## TO DO:
* Organize the categories better
* Create a CLI tool that will allow users to select tools from each category and generate a docker-compose file easier
* Add nginx & caddy
* documentation for general and advanced use
* 
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


## Traefik explanation
### Folders used:
* acme/
* traefik/
* ./ 

#### acme
This folder is where traefik will place a json file that contains the certs for each of your services. You will just need this folder for this file; it makes it easier to map it this way so that it can persist on your host, allowing Traefik to be restarted multiple times without getting hit with the "spam warning" from LEtsEncrypt

#### traefik
Place a folder within here named "dynamic" - this can be used for adding configuration files that tell traefik how to handle traffic destined for other servers. For example, I have ran out of RAM & CPU's on my main server, so to add more services to my homelab, I had to add a second server. however, you can only port forward to 1 IP (as far as I know) so I use this folder to add configs that tell traefik to point "gitlab.mydomain.com" to another server. This means that the network traffic goes to my router, then to server A, and then traefik sees this folder, and knows where to route this traffic (I tell it to go to server B). It works great!

One thing to remember if you are using the CloudFlare companion containers that auto-update your DNS Zone configuration to add new containers - when you use this dynamic configuration, the companion container will not automatically add containers running on a different server. In terms of what is best:
A. All your containers live on the same host, where the docker.sock is shared/present
B. When you fill up a host and need another server, you might want to explore Kubernetes (I reccomend rancher-server)
C. You can use this repo as an example; have as many services as comfortably possible on host A, and when full, setup containers on host B and for each service, add a configuration file to host A's `traefik/dynamic/` folder, and then add the service as a DNS entry in your domain provider.

#### ./
At the root of this repo, you see a "traefik.yml". This is the main conf file for traefik. 