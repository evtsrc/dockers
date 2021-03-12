# DOCKERFILE

- `docker build -t my_tomcat_app .`
	- kapak nola sortzen diren ikusi
	- denbora asko behar du
	- `docker images`

- `docker build -t tomcat_app -f Dockerfile_tomcat .`
	- irudi ofizialak erabiltzearen garrantzia: asko sinplifikatu
	- irudien pisua konparatu

- tomcat bertsioak
	- http://tomcat.apache.org
	- https://hub.docker.com/_/tomcat?tab=description&page=1&ordering=last_updated
	- 📢    **latest beti ez da azkenengo bertsioa!**
	
- `docker build -t tomcat10_app --build-arg TOMCAT_VERSION=10 -f Dockerfile_tomcat .`
	- **bertsio berriena ez da beti hoberena!**
	
- `docker build -t jetty_app -f Dockerfile_jetty .`
	- aldaketa txiki batekin beste zerbitzari baten probatu
	
- ETA EZ BADUT MVN NIRE ORDENAGAILUAN?

- `docker build -t tomcat_mvn_app -f Dockerfile_mvn_tomcat .`
	- konpilatu eta emaitza hedatu

- `docker build -t jetty_mvn_app -f Dockerfile_mvn_jetty .`
	- konpilatu eta emaitza hedatu

# KOMANDOAK
## mvn+tomcat jolasten
- **BUILD:** `docker build -t <name> .`
    > `[-t]` irudiaren izena

	> `[-f]` Dockerfile-a definitu
- **IMAGES:** `docker images`
- **RUN:** `docker run -d --name <name> -p 80:8080 image:latest` 
	> `[-d]` detached

	> `[--name]` edukiontziaren izena

	> `[-P]` portuak automatikoki mapeatu ⚠️ EXPORT 7000 ⚠️

	> `[-p]` mapeoa eskuz
- **LOGS:** `docker logs <name>`
- 💻 http://localhost:80
- klik batzuk egin

- **PS:** `docker ps`
    > `[-a]` geldi dauden edukiontziak
- **STOP/START:** `docker stop <name> && docker start <name>`
- **INSPECT:** `docker inspect <name>`	
	
- - - - - - - - - - - - - - - - - - - - 

## nginx
- **PULL:** `docker pull nginx`
- **RUN:** `docker run -P nginx` X 5
- 💻 http://localhost:XXXX
- **EXEC:** `docker exec -it XXXXX /bin/bash` 
	> `apt-get update && apt-get install vim`

	> `vi /usr/shared/naginx/html/index.html`
- 💻 http://localhost:XXXX
