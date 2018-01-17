# Purpose

A quick and simple local Postgres server for development or testing.

Postgres version: 10.1

## Notes

Postgres data files are created in your home directory (in `$HOME/docker-data/postgres`) and will
persist across container destruction and recreation.

This location can be changed by editing `volumes` in [docker-compose.yml](docker-compose.yml).

# Database initialization

Upon container creation, the database will be empty. You will need to do one or a combination of
the following:

- Manually create your database schema.
- Have your application create the database schema and run migration scripts.

## Automation via Docker

You can also have your database initialized during container creation via sql and bash scripts.

To have `*.sql` and `*.sh` scripts automatically run on container creation:

1. Place the script(s) in the [init](init) directory.
1. Edit [init/Dockerfile](init/Dockerfile) and specify each script appropriately.
	- One example is provided (commented out) for reference.

# Usage

Use the following information to connect to the database. These values may be changed in
[docker-compose.yml](docker-compose.yml).

- Hostname: localhost
- Port: 5440
- Admin username: postgres
- Admin password: (none)

# Convenience scripts

The following convenience scripts are provided:

- [start.sh](start.sh) - Start the container. Download and build images if necessary.
- [stop.sh](stop.sh) - Stop the container. Does not destroy anything.
- [destroy.sh](destroy.sh) - Kill and destroy the container. Does not delete any data.

# Troubleshooting

Validate the contents of [docker-compose.yml](docker-compose.yml):

	$ docker-compose config

View the status of the container:

	$ docker-compose ps

# Reference

- [Postgres image docs](https://store.docker.com/images/022689bf-dfd8-408f-9e1c-19acac32e57b?tab=description)

