# VOLUME ADIBIDEA

webgunean dago informazio guztia: https://hub.docker.com/_/mysql

`docker run -d -e MYSQL_DATABASE=book_manager -e MYSQL_ROOT_PASSWORD=root -e MYSQL_ROOT_HOST='%' -v /home/jkn/adibideak/book-manager/sql:/docker-entrypoint-initdb.d -v /home/jkn/adibideak/datadir:/var/lib/mysql --name docker-mysql mysql`

# NETWORK ADIBIDEA
kodea konpilatu
`gradel build`

Datu basea altsatu
`docker run -itd -e MYSQL_DATABASE=book_manager -e MYSQL_ROOT_PASSWORD=root -e MYSQL_ROOT_HOST='%' -v /home/jkn/adibideak/book-manager/sql:/docker-entrypoint-initdb.d -v /home/jkn/adibideak/datadir:/var/lib/mysql --name docker-mysql mysql`

> muntatu dugun volumen-a executatu dela ikusi
`docker logs docker-mysql -f`

> docker barnera sartu
`docker exec -it docker-mysql /bin/bash`

`mysql --user=root --password=root`
`use book_manager;`
`show tables;`
`select * from book;`

Aplikazioa altsatu
`docker run -d -P -p 10222:10222 --name app book-manager_book-manager-app`

Trazetan errorea ikusi
`docker logs app -f`

Sarea sortu
`docker network create multi-host-network`

Mysql sarera gehitu
`docker network connect --alias docker-mysql multi-host-network docker-mysql`

Aplikazioa sare barnean altsatu
`docker run -d -P -p 10222:10222 --network multi-host-network --name app book-manager_book-manager-app`

# DOCKER-COMPOSE
mysql adibidea [https://hub.docker.com/_/mysql] https://hub.docker.com/_/mysql

book_manager: java + mysql
