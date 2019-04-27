# Docker setup to play / work with PostgreSQL

## Overview

This setup installs a PostgreSQL server in current version and a matching pgAdmin4.

## Setup

- Please change the default postgres user password (variable POSTGRES_PASSWORD) in
  the postgres service.
- Also change the email address (PGADMIN_DEFAULT_EMAIL) and password (PGADMIN_DEFAULT_PASSWORD)
  in the phadmin service. The password should match the one above. The email address will be your
  login user name in pgAdmin.
- Have a look at the ports in the pgadmin service. I prefer to run it on port 80.
  But you might already have something else listening on that port.

## Startup

`docker-compose up -d` should build and start both services. In the course of
startup the shared volume directories `pgdata` (holds the PostgreSQL data to be
persistent between startups of the containers) and `pgadmin`(holds the pgAdmin4 config)
will be created. Don't delete them or you will lose data.

Check that everything is running as intended by issuing `docker-compose ps`.

When all looks good head over to your browser and open http://localhost (add a port if
you changed that from 80 to something else).

## Shutdown

`docker-compose stop` will stop both services. Your data will be save even if you delete
the containers, because it is stored in the two local folders created above.
