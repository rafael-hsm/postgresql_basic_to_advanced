# [PostgreSQL Administração do básico ao avançado](https://www.udemy.com/course/postgresql-administracao-do-basico-ao-avancado/?couponCode=KEEPLEARNING)
Notes for the Udemy course

## Comannds in WSL2
```bash
# Check version
psql --version
# Check service status
sudo service postgresql status
# If you don't have psql installed
sudo apt-get install postgresql postgresql-contrib
# Change user to postgres
sudo -i -u postgres
# Now you can acess postgres shell with:
psql
# To create a new user
CREATE ROLE <user> WITH LOGIN PASSWORD 'yourpassword';
# Make permission to new user
ALTER ROLE <user> CREATEDB;
# Or you need change password user 'postgres' for e.g.
sudo -i -u postgres
psql
ALTER ROLE postgres WITH PASSWORD 'postgres';
# Exit from psql
\q
# Connect with psql with new user
psql -U <user> -W
# Check status
sudo service postgresql status
# If necessary start service
sudo service postgresql start
```

## Tools in psql at Ubuntu/linux
```sql
-- To see all options
pg_<presstab>
-- Clusters relations
pg_lsclusters
>>> Ver Cluster Port Status Owner    Data directory              Log file
>>> 16  main    5432 online postgres /var/lib/postgresql/16/main /var/log/postgresql/postgresql-16-main.log
-- Create a new cluster (Collection of DB managed with unique instance of server psql): command -> version -> name
pg_createcluster 16 teste
-- Start cluster if it's down: command -> version -> name -> (start or stop or restart or reload)
pg_ctlcluster 16 teste start
-- Removing Cluster
pg_ctlcluster 16 teste2 stop
pg_dropcluster 16 teste2
```
### Creatind and mannagin Schemas/Databases
```bash
# Helper
\h create database
# Define a user how 
create database teste2 owner r4f43l
# After test remove database with
DROP DATABASE teste2;
```
![Owner Created](/img/define_owner.png)

- Schemas subdivision in path
```bash
# Create database
CREATE DATABASE teste2;
# acessing database with host
psql -U seu_usuario -d teste2 -h seu_host
# acessing database locally
psql -U postgres -d teste2
# List Schemas
\dn
# Create a new schema
CREATE SCHEMA rh;
# access table in schema public
\dt
# access especific schema
CREATE TABLE rhteste (id serial primary key);
CREATE TABLE rh.rhteste (id serial primary key);
# To set SCHEMA
SET SCHEMA 'rh':
\dt
```