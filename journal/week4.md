# Week 4 — Postgres and RDS

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
