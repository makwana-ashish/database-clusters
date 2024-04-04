
### Start MySQL docker services
> docker compose -f ./docker-compose.yml up -d


### Check all mysql services are running
> docker compose -f ./docker-compose.yml up -d

### Import your database (using mysql workbench or terminal)


### Setup repicator user

##### Connect to primary mysql database on your workbench or terminal

>SQL "CREATE USER 'replicator'@'%' IDENTIFIED BY 'replicaPassword';
GRANT REPLICATION SLAVE ON *.* TO 'replicator'@'%';
FLUSH PRIVILEGES;"


##### Connect to each replica and run below sql script

>SQL "CHANGE REPLICATION SOURCE TO
  SOURCE_HOST='mysql-primary',
  SOURCE_USER='replicator',
  SOURCE_PASSWORD='replicaPassword',
  SOURCE_AUTO_POSITION=1;
START REPLICA;"
