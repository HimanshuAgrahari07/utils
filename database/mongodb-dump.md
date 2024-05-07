# Mongodb Data Dump
## Installing mongodb CLI
Follow this [ref](https://www.mongodb.com/docs/manual/tutorial/install-mongodb-on-ubuntu/) to setup as per machine

For liunx mint (ubuntu)

```bash
sudo apt-get install gnupg curl
```
```bash
curl -fsSL https://www.mongodb.org/static/pgp/server-7.0.asc | \
   sudo gpg -o /usr/share/keyrings/mongodb-server-7.0.gpg \
   --dearmor
```
```bash
echo "deb [ arch=amd64,arm64 signed-by=/usr/share/keyrings/mongodb-server-7.0.gpg ] https://repo.mongodb.org/apt/ubuntu jammy/mongodb-org/7.0 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-7.0.list
```

```bash
sudo apt-get update
```

```bash
sudo apt-get install -y mongodb-org
```

## Taking db dump from mongodb database
- Go to desired folder directory
- Execute below command

Note: URI can be the uri for any mongodb database (cloud or any other db)

```bash
mongodump --uri mongodb+srv:y//servername:<password>@cluster.mxqe5.mongodb.net/Test_Database
```

It creates folder structure as `/dump/Test_Database`

## Restoring database dump to another mongodb server
- Goto parent directory of `/dump`
- Execute below query

```bash
mongorestore --uri 'mongodb://remotehost:27017/yourdatabase'
```


## Big database?
We can try by using gzip

### Take dump
```bash
mongodump --uri mongodb+srv:y//servername:<password>@cluster.mxqe5.mongodb.net/Test_Database --archive=<your file> --gzip
```
Here archive is the file /path/fileName

### Restore/Recreate
```bash
mongorestore --uri mongodb+srv:y//servername:<password>@cluster.mxqe5.mongodb.net/Test_Database --archive=<your file> --gzip
```

Here archive is the file /path/fileName


## Other ref
- https://medium.com/@mustafaburakaydiin/how-to-backup-and-restore-a-mongodb-database-in-a-docker-container-a7242ba0994f