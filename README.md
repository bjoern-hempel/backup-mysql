# backup mysql

A script to easily backup all your databases.

## A.) First usage

### A.1) installation

This application uses the friends of bash libraries (https://github.com/bjoern-hempel/friends-of-bash). Check that the libraries are available:

```
user$ friends-of-bash --version
friends-of-bash/v0.0.11
```

If you can see a similar friends of bash version output like above, you can now install this application:

```
user$ sudo -E friends-of-bash install "git@github.com:bjoern-hempel/backup-mysql.git"
```

If you don't have installed the friends of bash libraries, please install them first. In short:

```
user$ cd ~ && git clone git@github.com:bjoern-hempel/friends-of-bash.git && cd friends-of-bash
user$ sudo -E bin/install
user$ cd .. && rm -rf friends-of-bash
```

### A.2) add the mysql config file

```
user$ sudo mkdir /etc/backup-mysql
user$ sudo touch /etc/backup-mysql/config
user$ sudo vi /etc/backup-mysql/config
```

Content of /etc/backup-mysql/config:

```
MYSQL_USER="root"
MYSQL_PASSWORD="**********"
MYSQL_BACKUP_PATH="/var/backups/mysql"
LOCK_FILE="build.lock"
```

Make the file only readable by root user:

```
user$ sudo chmod -R 500 /etc/backup-mysql/config
```

### A.3) backup the database (the manual way)

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

### A.4) backup the database (the cronjob way)

```
user$ sudo touch /var/log/backup-mysql.log
user$ sudo chmod 664 /var/log/backup-mysql.log
user$ sudo chown root:root /var/log/backup-mysql.log
user$ sudo vi /etc/crontab
```

Content of /etc/crontab:

```
# MySQL backup every day one o'clock
00 01 * * * root backup-mysql >> /var/log/backup-mysql.log 2>&1
```
