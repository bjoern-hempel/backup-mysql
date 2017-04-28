# backup-mysql

A script to easily backup all your databases.

## A.) First usage

### A.1) installation

```
user$ cd /opt/
user$ sudo mkdir backup-mysql
user$ sudo chmod 775 backup-mysql
user$ sudo chown root:users backup-mysql
user$ git clone git@github.com:bjoern-hempel/backup-mysql.git
user$ sudo ./install
```

### A.2) add the mysql config file

```
user$ sudo mkdir /etc/backup-mysql
user$ sudo touch /etc/backup-mysql/config
user$ sudo chmod -R 500 /etc/backup-mysql/config
user$ sudo vi /etc/backup-mysql/config
```

Content of /etc/backup-mysql/config

```
MYSQL_USER="root"
MYSQL_PASSWORD="**********"
MYSQL_BACKUP_PATH="/var/backups/mysql"
LOCK_FILE="build.lock"
```

### A.3) backup the database

```
user$ sudo backup-mysql                                                                                                                                                        
[2017-04-28 15:45:14] [HEADER‧] START BACKUP MYSQL TABLES..
[2017-04-28 15:45:14] [INFO‧‧‧] Create folder /var/backups/mysql/2017/04/28/15-45-14
[2017-04-28 15:45:14] [INFO‧‧‧] Switch into folder /var/backups/mysql
[2017-04-28 15:45:14] [INFO‧‧‧] Lock backup folder. Write /var/backups/mysql/2017/04/28/15-45-14/build.lock.
[2017-04-28 15:45:14] [INFO‧‧‧] Dump database de.rsm-live.maco.team-mline.stage TO /var/backups/mysql/2017/04/28/15-45-14/de.rsm-live.maco.team-mline.stage.sql
[2017-04-28 15:45:14] [INFO‧‧‧] Zip sql file to /var/backups/mysql/2017/04/28/15-45-14/de.rsm-live.maco.team-mline.stage.sql.gz
[2017-04-28 15:45:14] [INFO‧‧‧] Dump database de.rsm-live.maco.team-mline.www TO /var/backups/mysql/2017/04/28/15-45-14/de.rsm-live.maco.team-mline.www.sql
[2017-04-28 15:45:14] [INFO‧‧‧] Zip sql file to /var/backups/mysql/2017/04/28/15-45-14/de.rsm-live.maco.team-mline.www.sql.gz
[2017-04-28 15:45:15] [INFO‧‧‧] Delete lock file
[2017-04-28 15:45:15] [INFO‧‧‧] Finish backup mysql script
```

### A.4) install cronjob

TODO ...
