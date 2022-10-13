# compose-homelab
Everything needed for a turnkey developer+devops+self-hosted system.

## Quick Start: 
1. `git clone https://github.com/timmay54/compose-homelab.git`
2. `cd compose-homelab`
3. `mv example.env .env`
4. `docker-compose up -d`

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
  * Kafka
  * NodeRed
  * Splunk
  * Vault
### Development:
  * VSCode (server)
  * Jupyter Notebook
  * MongoDB
  * Postgres
  * MySQL
  * Neo4J
  * Redis
### Hosting:
  * Traefik
  * Springboot backend (custom java project)
  * Tornado (Custom python project)

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
* Organize the categories better
* Create a CLI tool that will allow users to select tools from each category and generate a docker-compose file easier
* Add nginx & caddy
* documentation for general and advanced use
* 