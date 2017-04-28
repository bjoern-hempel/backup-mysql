# backup-mysql

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
