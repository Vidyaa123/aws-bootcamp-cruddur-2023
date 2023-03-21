# Week 4 — Postgres and RDS

### Create RDS Instance usng AWS CLI

```sh
$ aws rds create-db-instance \
  --db-instance-identifier cruddur-db-instance \
  --db-instance-class db.t3.micro \
  --engine postgres \
  --engine-version  14.6 \
  --master-username ${POSTGRES_MASTER_USERNAME} \
  --master-user-password ${POSTGRES_MASTER_PASSWORD} \
  --allocated-storage 20 \
  --availability-zone "${AWS_DEFAULT_REGION}" \
  --backup-retention-period 0 \
  --port ${POSTGRES_PORT} \
  --no-multi-az \
  --db-name cruddur \
  --storage-type gp2 \
  --publicly-accessible \
  --storage-encrypted \
  --enable-performance-insights \
  --performance-insights-retention-period 7 \
  --no-deletion-protection
 ```
 add a schema.sql file to cruddur ---- adding an extension
 
 ```sh
 psql cruddur < db/schema.sql -h localhost -U postgres
 ```
 
 Command to setup Connection URL:
 
 ```sh
 postgresql://[username[:password]@][netloc][:port][/dbname][?param1=value1&...]
 export CONNECTION_URL="postgresql://postgres:password@localhost:5432/cruddur"
 gp env CONNECTION_URL="postgresql://postgres:password@localhost:5432/cruddur"
 
```
### Shell Script to Connect to DB instance

Create anew folder 'bin' in backend-url and place all the bash scripts 

```sh
mkdir /workspace/aws-bootcamp-cruddur-2023/backend-flask/bin
```

```sh
export CONNECTION_URL="postgresql://postgres:pssword@127.0.0.1:5432/cruddur"
gp env CONNECTION_URL="postgresql://postgres:pssword@127.0.0.1:5432/cruddur"
```

inside db-connect file 

```sh
#! /usr/bin/bash

psql $CONNECTION_URL
```

To make the file executable:

```sh
chmod u+x bin/db-connect
```

To execute the script:
```sh
./bin/db-connect
```
### Shell Script to Create database

`bin/db-create`

```sh
#! /usr/bin/bash

NO_DB_CONNECTION_URL=$(sed 's/\/cruddur//g' <<<"$CONNECTION_URL")
createdb cruddur $NO_DB_CONNECTION_URL
```

### Shell Script to Load Schema

`bin/db-schema-load`

```sh
#! /usr/bin/bash

schema_path="$(realpath .)/db/schema.sql"

echo $schema_path

NO_DB_CONNECTION_URL=$(sed 's/\/cruddur//g' <<<"$CONNECTION_URL")
psql $NO_DB_CONNECTION_URL cruddur < $schema_path
```

### Make colourful print statements in bash scrips

https://stackoverflow.com/questions/5947742/how-to-change-the-output-color-of-echo-in-linux


```sh
CYAN='\033[1;36m'
NO_COLOR='\033[0m'
LABEL="db-schema-load"
printf "${CYAN}== ${LABEL}${NO_COLOR}\n"
```

### Shell Script to Drop Database

`bin/db-drop`

```sh
#! /usr/bin/bash

NO_DB_CONNECTION_URL=$(sed 's/\/cruddur//g' <<<"$CONNECTION_URL")
psql $NO_DB_CONNECTION_URL -c "DROP database cruddur;"
```
### Best Practices for securing Amazon RDS Postgres Database
1. Relational database ex: cstomer databse, credit card info, username & password
2. Makes sure where the database is created, check where the region is (**Best practice**)
3. Set the password for database - a secure one (**Best practise**)
4. 5432 - default port for Postgres
5. Check for security group (Inboubd & Outbound), region, port, publically accessible
6. Postgress app - check for the postgres database to test connection (DBeaver)
#### Security Best Practices for using RDS:
    - Use VPC to protect the RDS instamnce from unauthorized access
    - Meet compliance rewuirements for data
    - use in region wher you are legally allowed to hold user data
    - Use SCP to protect RDS from deletion, enforce encryption region lock etc....
    - Enable CloudTrail to trigger alerts on malicioud behaviour by anu identity
    - Enable Guardduty in the same region as RDS
    - Dont use default autentication(use IAM authentication, Kerberos etc)
    - Database user Lifecycle Management(create, delete & modify users)
    - User Access Lifecycle management (create, delete & revoke access to users)
    - RTestrict security groups to known IPs
    - Not internet accessible
    - Encryption in transit
    - Rotate Master password automatically by using Secret Manager
