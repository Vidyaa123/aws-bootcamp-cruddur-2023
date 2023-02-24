# Week 1 — App Containerization

## Tasks to Complete
- [**MY NOTES**](#my-notes)<br>
  ✅ [Chirag's Spending Considerations](#chirags-spending-considerations)<br>
  ✅ [Ashish's Container Security Best Practices](#ashishs-container-security-best-practices)<br>
  ✅ [Containerize Applications](#containerize-applications)<br>
  ✅ [Write a React Page for Notifications](#write-a-react-page-for-notifications)<br>
  ✅ [Run DynamoDB Local Container and ensure it works](#run-dynamodb-local-container-and-ensure-it-works)<br>
  ✅ [Run Postgres Container and ensure it works](#run-postgres-container-and-ensure-it-works)<br>

- [**MANDATORY CHALLENGES**](#mandatory-challenges)<br>
  ✅ [Document the Notification Endpoint for the OpenAPI Document](#document-the-notification-endpoint-for-the-openapi-document)<br>
  ✅ [Write a Flask Backend Endpoint for Notifications](#write-a-flask-backend-endpoint-for-notifications)<br>
  ✅ [Write a React Page for Notifications](#write-a-react-page-for-notifications)<br>
  ✅ [Run DynamoDB Local Container and ensure it works](#run-dynamodb-local-container-and-ensure-it-works)<br>
  ✅ [Run Postgres Container and ensure it works](#run-postgres-container-and-ensure-it-works)<br>

## My Notes
### Chirag's Spending Considerations 
#### Gitpod 
- check the pricing calculator on the gitpod.io website to stay within 50 hours of usage per month for free.
- Becomes inactive after 30 mins of no activity
- Last week I have consumed used most of my Gitpod free tier credits. I have just 49.99 cresits remaining for the rest of the month. 
- I have to make sure I stick to the time limit.

#### Github Codespaces
- 60 hours free usage for 2 core or 30 hours for 4 core.
- I havent started using codespaces yet, so should be fine for now

#### AWS Cloud9 
- free for 12 months
- dont use cloud9 if using t2.micro instance for any other purpose - it adds up the ec2 usage

#### AWS Cloudtrail
- avoid using Cloudtrail
- stores logs for 90 days
- do not opt for data and other insights.

### Ashish's Container Security Best Practices 
- practise of protecting applications hosted in containers
- Can be run in cloud or on-prem
- Container First Strategy
- Most applications are developed with Docker(Un-managed) / Managed AWS ECS / EKS
- reduces impact of breach because of application segregation
- In managed container services we just need to focus on few things - secucurity is taken care by the cloud providers
- managing container security needs practise
- Unmanaged Containers needs lots of hours / Managed there will be restrictions(deoednds on the cloud service provider)
#### Security Best Practices
- Apply security pacthes to host and daemon
- daemon and container should not run in root user mode
- keep the image size small - download is quick
- dont add secret files in any docker files
- and file system is read only - dont need container escape
- use seperate dabase for permanent storage (ex -RDS)
- use devsecops practises in the ci/cd pipeline
- ensure code has no vulnerabilities

#### Tools
- Using **Snyk Vulnerability** management tool
- **AWS Secret manager**
  - to store all secrets in AWS
  - can also use Hashicorp vault for holding secrets
- Docker Image Vulnerability Scanning - **Amazon Inspector** /**Clair**(Open source)


### Livestream - Docker with @James Spurin & @Edith Puclia
### Containerize Applications
- linuxstream.io
- dockerhub 
  -  a registry of containers public or private, free to use
  -  OCI standard
- 

## MANDATORY CHALLENGES


### Document the Notification Endpoint for the OpenAPI Document
<img width="1087" alt="Screenshot 2023-02-21 at 18 30 27" src="https://user-images.githubusercontent.com/15687491/220707270-a08eb3b1-3c3d-4db9-81b9-fea821731654.png">

### Write a Flask Backend Endpoint for Notifications

### Write a React Page for Notifications
<img width="1414" alt="Screenshot 2023-02-22 at 13 02 14" src="https://user-images.githubusercontent.com/15687491/220707099-bc264bba-51dd-4a64-9ec3-dc12276686b7.png">

### Run DynamoDB Local Container and ensure it works
<img width="1427" alt="Screenshot 2023-02-22 at 17 17 24" src="https://user-images.githubusercontent.com/15687491/220706819-b61ea2eb-2a7a-4c11-9109-0ee24388804e.png">

### Run Postgres Container and ensure it works
<img width="1386" alt="Screenshot 2023-02-22 at 17 12 14" src="https://user-images.githubusercontent.com/15687491/220707000-a71bbeb3-ec8d-4abe-9b14-1f749d5ff68d.png">

 
