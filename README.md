# nodejs-docker-basic

With project we will create an application of a static website that uses the [Express](https://expressjs.com/) framework and [Bootstrap](https://getbootstrap.com/). 

Then we will use the [Docker](https://www.docker.com/) platform to create an `application image`. Then we will package and run the application as `containers` using that image and push in to [Docker Hub](https://hub.docker.com/) for future use. Finally, we will pull the stored image from the Docker Hub repository and build another container, demonstrating how we re-create and scale the application.  

## Walkthrough
To getting understand about this project, you will need to following this tutorial:
- One Ubuntu 18.04 server, set up following this [**Initial Server Setup guide**](https://www.digitalocean.com/community/tutorials/initial-server-setup-with-ubuntu-18-04).
- Docker installed on your server, following Steps 1 and 2 of [**How To Install and Use Docker on Ubuntu 18.04**](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-on-ubuntu-18-04).
- Node.js and npm installed, following these instructions on [**installing with the PPA managed by NodeSource**](https://www.digitalocean.com/community/tutorials/how-to-install-node-js-on-ubuntu-18-04#installing-using-a-ppa).
- A Docker Hub account. For an overview of how to set this up, refer to this introduction on [**getting started with Docker Hub**](https://docs.docker.com/docker-hub/).

## Running the packages
The application images has been pushed in Docker Hub. You can use this images by now.

Login to your Docker Hub:

```bash
docker login -u your_docker_hub_username
```

You can now pull the application image from Docker Hub:

```bash
docker pull danangsukma/nodejs-docker-basic
```
```bash
# Sample Output:
Using default tag: latest
latest: Pulling from danangsukma/nodejs-docker-basic
e7c96db7181b: Pull complete
50958466d97a: Pull complete
56174ae7ed1d: Pull complete
284842a36c0d: Pull complete
9261e03ba7aa: Pull complete
2e57fb26e018: Pull complete
20ff2dcea87f: Pull complete
47c93d31e9d1: Pull complete
Digest: sha256:1bb39800d4a1221a39084dc55ecde01affe0b205cf088d712fb746afb927baa3
Status: Downloaded newer image for danangsukma/nodejs-docker-basic:latest
docker.io/danangsukma/nodejs-docker-basic:latest
```

List your images once again:

```bash
docker images
```

You will see your application image:

```bash
# Sample Output
REPOSITORY                        TAG                 IMAGE ID            CREATED             SIZE
danangsukma/nodejs-docker-basic   latest              b6c0ade3dec6        24 minutes ago      78.8MB
```

You can now rebuild your container using the command

```bash
docker run --name nodejs-docker-basic -p 80:8080 -d danangsukma/nodejs-docker-basic
```

List your running containers:

```bash
docker ps
```

```bash
# Sample Output
CONTAINER ID        IMAGE                             COMMAND                  CREATED             STATUS              PORTS                  NAMES
7df876904002        danangsukma/nodejs-docker-basic   "docker-entrypoint.s…"   37 seconds ago      Up 33 seconds       0.0.0.0:80->8080/tcp   nodejs-docker-basic
```

Visit `http://your_host_ip` once again to view your running application.

## Next steps
- [**How To Install Docker Compose on Ubuntu 18.04.**](https://www.digitalocean.com/community/tutorials/how-to-install-docker-compose-on-ubuntu-18-04)
- [**How To Migrate a Docker Compose Workflow to Kubernetes**](https://www.digitalocean.com/community/tutorials/how-to-migrate-a-docker-compose-workflow-to-kubernetes)
- Completing the series of tutorial [**From Containers to Kubernetes with Node.js**](https://www.digitalocean.com/community/tutorial_series/from-containers-to-kubernetes-with-node-js).  The series also includes information on deploying your app with Docker Compose using an Nginx reverse proxy and Let’s Encrypt.

If you are interested in other Docker-related topics, here is the [Docker tutorials](https://www.digitalocean.com/community/tags/docker/tutorials) for recommended reading.
