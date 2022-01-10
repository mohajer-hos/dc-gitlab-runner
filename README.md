## Run a gitlab-runner instance with docker-compose
[![Build Status](https://files.ariadata.co/file/ariadata_logo.png)](https://ariadata.co)

![](https://img.shields.io/github/stars/ariadata/dc-gitlab-runner.svg)
![](https://img.shields.io/github/watchers/ariadata/dc-gitlab-runner.svg)
![](https://img.shields.io/github/forks/ariadata/dc-gitlab-runner.svg)

> This needs `DockerHost` : [install from here](https://github.com/ariadata/ubuntu-sh) .

---
#### 1- Clone these repository to your system :
```sh
git clone https://github.com/ariadata/dc-gitlab-runner.git && cd dc-gitlab-runner && rm -rf .git
```
#### 2- Run docker-compose file by using :
```sh
docker-compose up -d
```
#### 3- Login to `gitlab-runner` container by :
```sh
docker exec -it dc-gitlab-runner bash
```
#### 4- Register your runner by :
```sh
gitlab-runner register
```
> Fill the requested information
> 
> *Note sample* : for tags you can use `docker,linux,ubuntu` (for shared add `shared` too!)
> 
> *Note sample* : for executor enter `docker`
> 
> *Note sample* : for default docker image enter `ubuntu:latest`

#### 5- restart your instance by :
```sh
gitlab-runner restart
```
#### 6- exit from container by `exit` command.

#### 7- (optional) Remove unused docker images by runnig this command anytime in your dockerhost:
```sh
docker system prune -af
```
Or you can set cron for do this for example once per day at midnight by :
```sh
crontab -l | { cat; echo "0 0 * * * docker system prune -af >/dev/null 2>&1"; } | crontab -
sudo systemctl restart cron
```
#### 8- (optional) You can edit config file of your instance :
```sh
sudo nano config/config.toml
docker exec -it gitlab-runner gitlab-runner restart
```

Done!
