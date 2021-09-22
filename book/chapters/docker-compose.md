# Docker Compose

So far we have used the `docker` command with a variety of options to build and run containers. Whilst this is a good way to get started -- and if you are using Docker you still need to understand the command line options -- it doesn't scale well to situations such as having lots of containers which interact with each other or where you want to regularly rebuild containers (which is one of the key selling points of containers).

Fortunately, there is a tool called Docker Compose (`docker-compose`) which allows you to specify options in a configuration file and then run a single command to start or stop all the containers.

## Basic phpinfo example

Create a new directory with the following files:

index.php:

```php
#include "../examples/basic-docker-compose/index.php"

```

docker-compose.yml:

```yaml
#include "../examples/basic-docker-compose/docker-compose.yml"

```

Build and run with:

```bash
$ docker-compose up --build -d
```

Visit [http://localhost:8080](http://localhost:8080) in a web browser and you should see the familiar PHP version and build details.

## Overrides file

In addition to `docker-compose.yml`, you can also specify an overrides file, which by convention is named `docker-compose.override.yml`. This allows you to have a base configuration which applies to all of your environments (production, staging, development etc.), whilst providing per-environment options such as hostnames.

In addition, an overrides file allows you to store credentials without committing them to version control (your main `docker-compose.yml` should be in version control so that other developers receive it when cloning the repository).

## Docker Compose from now on

Whilst there may be instances where you need to run Docker on the command line (e.g. to login to a running container), for the rest of this book we will primarily be using Docker Compose.