# my-linux-references

## Docker / MEAN Stack

### Running mongodb in a Docker container

Create a data directory to attach into the mongo db container as a volume and then run / pull the Docker monogo image with the following options:
- expose port 27017 to local machine
- map a volume from ~/data from local machine to /data/db in container
- name container 'db'

```
mkdir ~/data

docker run -p 27017:27017 -v ~/data:/data/db -d --name db mongo
```

### Testing mongodb container and data volume from localhost

Ensure you have a mongodb client installed on local machine.

For Ubuntu use `sudo apt-get install mongodb-clients`
 
Run mongoDB client with `mongo`

Run `show collections` to check the collection

Create a test collection with `db.createCollection('locally-created-test)`

Now to ensure that your container is accessing the correct volume exec bash on the container, run the mongo client in the container and check the collections:

```
docker exec -it mongo bash

mongo

show collections
```

You should then see the collection you've created on the local machine inside the container.

### Building the MEANJS container image

Clone meanjs github repo to local:

```
    cd <dev directory>

    git clone https://github.com/meanjs/mean.git

    cd mean
```

Build Dockerfile `docker build -t mean .`

Run docker container `docker run -p 3000:3000 --link db:db_1 mean`


### Access the MEANJS sample page 

If all builds ok then access the sample app by using http://localhost:3000 or use the public IP in place of localhost


