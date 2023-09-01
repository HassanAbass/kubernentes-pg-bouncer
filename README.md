# kubernentes-pg-bouncer
# PostgreSQL with PgBouncer and Adminer on Kubernetes

This repository contains Kubernetes configuration files to deploy a PostgreSQL database with PgBouncer as a connection pooler and Adminer as a web-based database management tool. This setup is useful for managing database connections and accessing the database through a convenient web interface.

## Prerequisites

Before deploying this stack, ensure you have the following prerequisites:

1. Kubernetes cluster up and running.
2. `kubectl` command-line tool configured to access your cluster.
3. Basic knowledge of Kubernetes concepts.


## Setup
In case you are using WSL you will need to create `postgres-data` directory, then mount it, otherwise just create the postgres-data directory and fill the path in the persistance volume local path

1. Create the following folder structure on your local system:

    **Windows:**   `c:/db`

        If you're using WSL with Docker desktop try using `/mnt/c/temp/data/db` or `/run /run/desktop/mnt/host/wsl/postgres-data (depending on your WSL version and setup)
    **Linux:** `/postgres-data`

    ** if you using `WSL` with `docker-desktop` you might need to mount the volume**

        mount --bind /home/$USER/postgres-data /mnt/wsl/postgres-data
        
2. fill the create directory path in the persistance volume local path

3. Run the containers using the command:

    ```
    kubectl create -f deployment.yml
    ```

## Testing
1. Using the terminal to access postgres through pg bouncer
    ```bash
   psql -h localhost -p 6432 -U postgres
   > insert password(secret)
1. Using Adminer(light DB management tool), open it using `8080` port [localhost:8080](`http://localhost:8080`)



