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
 To check if the connection is working add a schema.sql file to cruddur ---- adding an extension
 
 ```sh
 psql cruddur < db/schema.sql -h localhost -U postgres
 ```
 
 Command to setup Connection URL:
 
 ```sh
 postgresql://[username[:password]@][netloc][:port][/dbname][?param1=value1&...]
 export CONNECTION_URL="postgresql://postgres:password@localhost:5432/cruddur"
 gp env CONNECTION_URL="postgresql://postgres:password@localhost:5432/cruddur"
 
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
