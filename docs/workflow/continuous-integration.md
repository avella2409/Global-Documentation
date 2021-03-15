# Continuous Integration

## Private git at start
- Git machine user, collaborator of project
- Machine user have ssh key associated

## Dockerize at start with logging in mind
- Fluent bit
- Multiple process docker : startup.sh script
- Elasticsearch

## Jenkins Jobs at start
- Build Job
- Release Job
- Push Job

## Jenkins env variable
- AWS Region
- Tools : Maven/Java

## Jenkins credentials
- AWS Access/Secret
- RabbitMQ secret
- etc...

## Problem ?
- docker.sock permission > Go root and chmod 777 docker.sock
- Git permission > Go /var/lib/jenkins/.ssh/. Add "config" file with git host pointing to ssh key of git machine user (See [Deploy key git documentation](https://docs.github.com/en/developers/overview/managing-deploy-keys))
- Need to use jenkins user ?

Go root
```bash  
sudo -s 
```
Then change to jenkins user
```bash 
su - jenkins -s /bin/bash
```