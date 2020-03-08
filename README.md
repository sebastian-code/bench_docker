# Frappe on Docker

[![Build Status](https://travis-ci.com/frappe/frappe_docker.svg)](https://travis-ci.com/frappe/frappe_docker)

This is a repo were I will try to create a better Docker setup for your development workflow with the Frappe framework.

## Getting Started

These instructions will get you a copy of the project up and running on your local machine for development and testing purposes.

Keep in mind than this container is not suited for a production environment.

### Build the container and initialize the bench

**Note:** These instructions assume you have both  [Docker](https://docs.docker.com/engine/installation)  and [Docker Compose](https://docs.docker.com/compose/install/) installed on your system.

1. Clone this repo and change your working directory to it:

    ```bash
    git clone git@github.com:sebastian-code/bench_docker.git
    cd bench_docker/
    ```

2. Build and start the container, and initialize the bench:

    ```bash
    ./dbench setup docker
    ./dbench init
    ```

    **Note:** This will take a while, as docker will now build the container.

3. Add a new site and start Frappe:

    ```bash
    ./dbench new-site site1.local
    ./dbench setup hosts
    ./dbench start
    ```

4. Use Frappe:
    Open your browser to `localhost:8000/login`. Then log in using the username `Administrator` and the password `admin`.

### Basic Usage of `./dbench`

**IMPORTANT: Always make sure that your current directory is the root directory of the repo (i.e. `frappe_docker/`)**

- `./dbench`: Launches you into an interactive shell in the container as the user `frappe`.

- `./dbench setup docker [ stop | down ]`: Starts and builds the docker containers using `docker-compose up -d`.
  - `stop`: Stops the containers with `docker-compose stop`.
  - `down`: Deletes the containers and the corresponding volumes with `docker-compose down`.

- `./dbench setup hosts`: Adds all sites to the containers hosts file.
  **Note:** Run this after you've added a new site to avoid errors.

- `./dbench -c frappe | root <command to run>`: Runs a command in the container, as the selected user.

- `./dbench -h`: Shows this help message.

- `./dbench <bench command>`: Runs a command in bench (i.e. Running `./dbench new-site site1.local`, will run `bench new-site site1.local` in the container).

## Contributing

Feel free to contribute to this project and make it better.

## License

This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details
