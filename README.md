# Docker2Compose
## How to install
* docker & docker-compose required (_Install the Docker & Docker-compose_: `curl -sL bit.ly/startdocker |bash`)
```
curl -sL bit.ly/dcc_ > ./dcg
chmod 755 ./dcg
```

## How to use
 * Command sample

```
ex)
./dcg sudo docker run -d --restart=always --name oracle_xe -p 30022:22 -p 1521:1521 -e ORACLE_ALLOW_REMOTE=true wnameless/oracle-xe-11g

version: '2'
services:
  oracle_xe:
    image: wnameless/oracle-xe-11g
    environment:
      - "ORACLE_ALLOW_REMOTE=true"
    ports:
      - "30022:22"
      - "1521:1521"
    ## options as below
    restart: always
```

 * Result as below

```
tree

├── dcg
├── README.md
└── oracle_xe
    └── docker-compose.yml
    
cd oracle_xe && docker-compose up -d
```

## You can make a docker-compose stack as below(Manually)
* Sonarqube+MySQL stack
```
version: '2'
services:
  sonarqube:
    image: sonarqube
    environment:
      - "SONARQUBE_JDBC_USERNAME=sonarqube"
      - "SONARQUBE_JDBC_PASSWORD=sonarqube"
      - "SONARQUBE_JDBC_URL=jdbc:mysql://{ip}:3306/sonarqube?useUnicode=true&characterEncoding=utf8"
    ports:
      - "9000:9000"
      - "9092:9092"
    ## options as below
    restart: always
    links:
      - db
  db:
    image: mysql:5.7
    environment:
      - MYSQL_ROOT_PASSWORD=sonarqube
      - MYSQL_DATABASE=sonarqube
      - MYSQL_USER=sonarqube
      - MYSQL_PASSWORD=sonarqube
    volumes:
      - ./datadir:/var/lib/mysql
```
