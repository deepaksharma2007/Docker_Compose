# WordPress with MySQL Docker Compose Configuration

This Docker Compose configuration sets up a WordPress application connected to a MySQL database. It provides an easy-to-use environment for development or testing purposes.

## Prerequisites

Ensure that you have the following installed on your system:

- Docker Engine
- Docker Compose

## Usage

1. Clone this repository:

    ```sh
    git clone https://github.com/deepaksharma2007/Docker_Compose.git 
    ```

2. Navigate to the project directory:

    ```sh
    cd Docker_Compose
    ```

3. Run the Docker Compose command:

    ```sh
    docker-compose up -d
    ```

## Services

The `docker-compose.yml` file configures two services:

### Database (db)

- **Container Name:** mydb1
- **Image:** mysql:latest
- **Volumes:** /data:/var/lib/mysql
- **Environment Variables:**
  - MYSQL_ROOT_PASSWORD: redhat
  - MYSQL_DATABASE: mydb
  - MYSQL_USER: deepak
  - MYSQL_PASSWORD: redhat

### WordPress (wp)

- **Depends On:** db
- **Container Name:** mywp
- **Image:** wordpress:latest
- **Ports:** 8080:80
- **Environment Variables:**
  - WORDPRESS_DB_HOST: mydb1
  - WORDPRESS_DB_USER: deepak
  - WORDPRESS_DB_PASSWORD: redhat
  - WORDPRESS_DB_NAME: mydb
- **Volumes:** /wordpress:/var/www/html

## some more keywords:
**1. services**
The services section is where you define the containers (or services) that make up your application. Each service represents a containerized application component. Services can be built from an image, or built from a Dockerfile.

**2. depends_on**
The depends_on keyword is used to specify the dependencies between services. It ensures that one service starts only after the services it depends on are started. However, it does not wait for the services to be "ready" before starting.

**3. networks**
The networks keyword is used to define custom Docker networks for the services. Docker networks allow containers to communicate with each other. In this configuration, a custom network named deep_net is defined with the subnet 172.16.238.0/24.

**4. volumes**
The volumes keyword is used to specify volumes that should be mounted inside the container. Volumes allow data to persist beyond the lifetime of a container and can be shared between containers. In this configuration, the MySQL data directory (/var/lib/mysql) and the WordPress files (/var/www/html) are mounted as volumes.

**Other Keywords**
***container_name:*** Specifies the name of the container. If not provided, Docker Compose generates a name based on the service name.

***image:*** Specifies the Docker image to use for the service.

***ports:*** Specifies the port mappings between the host and the container.

***environment:*** Specifies environment variables to pass to the container.

***driver:*** Specifies the network driver to use. In this configuration, the default bridge driver is used.

***ipam:*** Specifies the IP address management configuration for the network.

These keywords provide configuration options to customize the behavior and setup of Docker containers within a Docker Compose configuration file. They allow you to define the structure of your application, specify dependencies between services, configure networking, manage volumes, and more.
## Accessing WordPress

After running the Docker Compose command, you can access the WordPress application in your web browser at [http://localhost:8080](http://localhost:8080).

## Network Configuration

The Docker Compose file sets up a custom Docker network named `deep_net` with the subnet `172.16.238.0/24` for communication between the containers.

