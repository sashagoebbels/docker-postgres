# Docker setup to play / work with PostgreSQL

## Overview

This setup installs a PostgreSQL server in current version and a matching pgAdmin4.

## Setup

- Please change the default postgres user password (variable POSTGRES_PASSWORD) in
  the postgres service.
- Also change the Email adress (PGADMIN_DEFAULT_EMAIL) and password (PGADMIN_DEFAULT_PASSWORD)
  in the phadmin service. The password should match the one above.
- Have a look at the ports in the pgadmin service. I prefer to run it on port 80.
  But you might already have something else listening on that port.

## Startup

`docker-compose up -d` should build and start both services. In the course of
startup the shared volume directories `pgdata` (holds the PostgreSQL data to be
persistent between startups of the containers) and `pgadmin`(holds the pgAdmin4 config)
will be created. Don't delete them or you will lose data.