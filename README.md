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

## Accessing WordPress

After running the Docker Compose command, you can access the WordPress application in your web browser at [http://localhost:8080](http://localhost:8080).

## Network Configuration

The Docker Compose file sets up a custom Docker network named `deep_net` with the subnet `172.16.238.0/24` for communication between the containers.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.
