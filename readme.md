- [PostgreSQL - Advanced Open Source Relational Database](https://www.postgresql.org/)
  - [Documentation](https://www.postgresql.org/docs/current/index.html)
  - [Tutorials](https://www.postgresql.org/docs/current/tutorial.html)
  - [How to Install PostgreSQL and pgAdmin4 in Ubuntu 20.04](https://tecadmin.net/how-to-install-postgresql-in-ubuntu-20-04/)

- Installing PostgreSQL in Ubuntu 20.04
  - Step 1 - Installation 
```bash
  sudo sh -c 'echo "deb http://apt.postgresql.org/pub/repos/apt $(lsb_release -cs)-pgdg main" > /etc/apt/sources.list.d/pgdg.list'
  wget --quiet -O - https://www.postgresql.org/media/keys/ACCC4CF8.asc | sudo apt-key add -
  sudo apt-get update
  sudo apt-get -y install postgresql postgresql-contrib
  sudo systemctl status postgresql 
```
  - Step 2 - Connection to PostgreSQL
```bash
  sudo -u postgres psql
```
  - Step 3 - Securing PostgreSQL by creating a password for `postgres` user account
```bash
  sudo passwd postgres
```
  - Step 4 - Create a secure/strong password for `PostgreSQL` admin database user/role
```bash
  su - postgres 
  psql -c "ALTER USER postgres WITH PASSWORD 'secure_password_here';" 
  exit
  sudo systemctl restart postgresql 
```
  - Step 5- Install pgAdmin
```bash
  curl https://www.pgadmin.org/static/packages_pgadmin_org.pub | sudo apt-key add -
  sudo sh -c 'echo "deb https://ftp.postgresql.org/pub/pgadmin/pgadmin4/apt/focal pgadmin4 main" > /etc/apt/sources.list.d/pgadmin4.list'
  sudo apt-get update
  sudo apt-get -y install pgadmin4
  sudo systemctl restart postgresql 
```

- As personal preference, add these settings to `.bashrc` postgres-status, postgres-start, postgres-stop, postgres-restart

```bash
   alias postgres-restart='sudo systemctl restart postgresql'
   alias postgres-start='sudo systemctl start postgresql'
   alias postgres-stop='sudo systemctl stop postgresql'
   alias postgres-status='sudo systemctl status postgresql'
   alias postgres-enable='sudo systemctl enable postgresql'
   alias postgres-disable='sudo systemctl disable postgresql'
   alias postgres-disable='sudo systemctl is-active postgresql'
   alias postgres-disable='sudo systemctl is-enabled postgresql'
```

- Additional PostgreSQL references
  - [Install PostgreSQL Linux](https://www.postgresqltutorial.com/install-postgresql-linux/)
  - [PostgreSQL Sample Database](https://www.postgresqltutorial.com/postgresql-sample-database/)
  - [Create new local server in pgadmin](https://stackoverflow.com/questions/53267642/create-new-local-server-in-pgadmin)
  - [How to install pgcrypto module on a postgres DB](https://stackoverflow.com/questions/52630876/how-to-install-pgcrypto-module-on-a-postgres-db/52637460)

- Sample postgres data sets
  - [Load PostgreSQL Sample Database](https://www.postgresqltutorial.com/load-postgresql-sample-database/)
```bash
  unzip ~/Downloads/dvdrental.zip
  psql
```
```postgresql
  postgres=# create database dvdrental;
  postgres=# \q
```
```bash
  pg_restore -h localhost -U postgres -d dvdrental ~/Downloads/dvdrental.tar
```
