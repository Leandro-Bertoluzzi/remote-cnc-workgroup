<h1 align="center">Remote CNC manager</h1>

<p align="center">
  <img alt="Github top language" src="https://img.shields.io/github/languages/top/Leandro-Bertoluzzi/remote-cnc-workgroup?color=56BEB8">

  <img alt="Github language count" src="https://img.shields.io/github/languages/count/Leandro-Bertoluzzi/remote-cnc-workgroup?color=56BEB8">

  <img alt="Repository size" src="https://img.shields.io/github/repo-size/Leandro-Bertoluzzi/remote-cnc-workgroup?color=56BEB8">

  <img alt="License" src="https://img.shields.io/github/license/Leandro-Bertoluzzi/remote-cnc-workgroup?color=56BEB8">
</p>

<!-- Status -->

<h4 align="center">
	🚧 Remote CNC manager 🚀 Under construction...  🚧
</h4>

<hr>

<p align="center">
  <a href="#dart-about">About</a> &#xa0; | &#xa0;
  <a href="#sparkles-features">Features</a> &#xa0; | &#xa0;
  <a href="#rocket-technologies">Technologies</a> &#xa0; | &#xa0;
  <a href="#white_check_mark-requirements">Requirements</a> &#xa0; | &#xa0;
  <a href="#checkered_flag-starting">Starting</a> &#xa0; | &#xa0;
  <a href="#memo-license">License</a> &#xa0; | &#xa0;
  <a href="https://github.com/Leandro-Bertoluzzi" target="_blank">Authors</a>
</p>

<br>

## :dart: About

Implementation of web app + API to remotely monitor and manage an Arduino-based CNC machine.

## :sparkles: Features

:heavy_check_mark: REST API\
:heavy_check_mark: SQL database management\
:heavy_check_mark: Real time monitoring of CNC status

## :rocket: Technologies

The following tools were used in this project:

-   Web app, frontend: [Next.js](https://nextjs.org/) with [Typescript](https://www.typescriptlang.org/)
-   Containerization: [Docker](https://www.docker.com/)
-   API: [FastAPI](https://fastapi.tiangolo.com/)
-   Database: [PostgreSQL](https://www.postgresql.org/)
-   ORM: [SQLAlchemy](https://www.sqlalchemy.org/)
-   DB migrations: [Alembic](https://alembic.sqlalchemy.org/en/latest/)
-   Server, reverse proxy: [Nginx](https://www.nginx.com/)

## :white_check_mark: Requirements

Before starting :checkered_flag:, you need to have installed:

-   [Node](https://nodejs.org/en/) to run the Next.js app in developer mode and generate the frontend pages for production,
-   [Python](https://www.python.org/) to run the backend,
-   [Nginx](https://www.nginx.com/) to configure a production server and
-   [PostgreSQL](https://www.postgresql.org/)

Alternatively, if you have [Docker](https://www.docker.com/) installed, you can build and run the whole application, both in development and production mode, without installing the aforementioned programs.

More information about how to init your development environment [here](./docs/development.md).

## :checkered_flag: Starting

```bash
# Clone this project
$ git clone --recurse-submodules https://github.com/Leandro-Bertoluzzi/remote-cnc-workgroup

# Access
$ cd remote-cnc-workgroup

# Run the project
$ docker compose up

# The first time, you may want to run DB migrations
# Command to run the DB schema migrations
$ docker exec remote-cnc-api bash -c "cd core && alembic upgrade head"

# You can access the web app in <http://localhost:3000>
# The API will initialize in <http://localhost:8000>
# You can access adminer through <http://localhost:8080>
```

You can also run the project in `production` mode:

```bash
# Run the project in production mode
$ docker-compose -f docker-compose.yaml -f docker-compose.production.yaml up -d
```

## :wrench: Running tests

### API

- All tests:

```bash
# We run the command inside the container
$ docker exec -it remote-cnc-api make tests
```

### App

- Linter:

```bash
$ docker exec -it remote-cnc-app npm run lint:check
```

- Unit tests:

```bash
$ docker exec -it remote-cnc-app npm run test:unit
```

## :checkered_flag: Deployment

In order to deploy the app, you must export it as a static site. To do so, you must run the following command in development mode:

```bash
$ docker exec -it remote-cnc-app npm run build
```

Then, if you want, you can deploy the project with docker-compose:

```bash
# Run the project in production mode
$ docker-compose -f docker-compose.yaml -f docker-compose.production.yaml up -d
```

Also, take into account that you must update the environment variables.

A more comprehensive guide about the deployment [here](./docs/deployment.md).

## :memo: License

This project is under license from MIT. For more details, see the [LICENSE](LICENSE.md) file.

## :writing_hand: Authors

Made with :heart: by <a href="https://github.com/Leandro-Bertoluzzi" target="_blank">Leandro Bertoluzzi</a> and Martín Sellart.

<a href="#top">Back to top</a>
