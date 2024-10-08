# Install-Apache-Superset-in-Docker-Container
This repository will help you to install apache superset in docker container.

## Follow the steps

Make sure Docker and Git is installed in your system.

 #### 1. Clone Superset's GitHub repository

 [apache / superset repository](https://github.com/apache/superset)

 ```
 git clone --depth=1  https://github.com/apache/superset.git

 ```

#### 2. Go to Superset Directory

```
cd superset/
```

#### 3. Run docker compose
```
export TAG=3.1.1
docker compose -f docker-compose-image-tag.yml up
```
Great, now you can access Apche Superset at you local host
```
http://127.0.0.1:<port number>/
```
*default port number is '8088'* ``` http://127.0.0.1:8088/ ```

#### username: ```admin```

#### password: ```admin```

## Error

If the above steps results in error, then follow below.

#### error 1: *unknown shorthand flag: 'f' in -f*

This means your **docker** and **docker compose** is outdated. Update **docker** and **docker compose** to the latest version and then try below command:

```
export TAG=3.1.1
docker compose -f docker-compose-image-tag.yml up
```
OR

without upgrade use below command:

```
export TAG=3.1.1
docker-compose -f docker-compose-image-tag.yml up
```

#### error 2: *validating /superset/docker-compose-image-tag.yml: services.db.env_file.0 must be a string*

open ``` docker-compose-image-tag.yml ``` file.

replace all the occurances of below

```
env_file:
      - path: docker/.env # default
        required: true
      - path: docker/.env-local # optional override
        required: false
```
with this

```
env_file: docker/.env 
```
or 
```
env_file:
  - docker/.env
```
whatever works for you.

Then run below command:
```
export TAG=3.1.1
docker-compose -f docker-compose-image-tag.yml up
```
or
```
export TAG=3.1.1
docker compose -f docker-compose-image-tag.yml up
```
depending on your version.


If your error resolved properly then you can access your **Apache Superset** below:

```
http://127.0.0.1:<port number>/
```
*default port number is '8088'* ``` http://127.0.0.1:8088/ ```


## useful commands

**note**: if '*docker-compose*' not working then try '*docker compose*'.

* run below to start container in detachable mode, (*-d* used for detachable mode).
```
docker-compose -f docker-compose-image-tag.yml up -d
```

* view logs.
```
docker-compose -f docker-compose-image-tag.yml logs
```

* stop all the container simultaneously.
```
docker-compose -f docker-compose-image-tag.yml stop
```

* start all the container simultaneously.
```
docker-compose -f docker-compose-image-tag.yml start
```
**note**: you can replace '*docker-compose-image-tag.yml* ' with your yml file.

* see all the running containers.
```
docker ps
```
* see all the created containers.
```
docker ps -a
```



## Documentation
Official documentation for installation: 
[Documentation](https://superset.apache.org/docs/installation/docker-compose/)

## If you liked this repository

* Dont't forget to give this repository a 🌟
