# How to Install PostgreSQL

## Install PostgreSQL using the `apt` package manager

`$ sudo apt update`

`$ sudo apt install postgresql postgresql-contrib`

## Log into the `postgres` account

`$ sudo -i -u postgres`

## Access Postgres prompt

`$ psql`

## Create new Postgres Role

If you are logged in as the postgres account, you can create a new user by typing:

`postgres@server:~$ createuser --interactive`

If, instead, you prefer to use sudo for each command without switching from your normal account, type:

`$ sudo -u postgres createuser --interactive`

## Create database for new user

Another assumption that the Postgres authentication system makes by default is that for any role used to log in, that role will have a database with the same name which it can access.

If you are logged in as the postgres account:

`postgres@server:~$ createdb <username>`

If you prefer to use sudo for each command without switching from your normal account, you would type:

`$ sudo -u postgres createdb <username>`

## Sign in to Postgres Prompt with new Role
To log in with ident based authentication, you'll need a Linux user with the **same name** as your Postgres role and database.

Once you are logged in to the shell as the Linux user with the **same name** as your Postgres role and database:

`$ psql`