# Docker2Compose
## How to install

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
```

