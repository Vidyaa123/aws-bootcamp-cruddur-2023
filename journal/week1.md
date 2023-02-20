# Week 1 — App Containerization

## Tasks to Complete
- [**MY NOTES**](#my-notes)<br>

- [**MANDATORY CHALLENGES**](#mandatory-challenges)<br>
  ⬛ [Containerize Applications](#containerize-applications)<br>
  ⬛ [Document the Notification Endpoint for the OpenAI Document](#document-the-notification-endpoint-for-the-openai-document)<br>
  ⬛ [Write a Flask Backend Endpoint for Notifications](#write-a-flask-backend-endpoint-for-notifications)<br>
  ⬛ [Write a React Page for Notifications](#write-a-react-page-for-notifications)<br>
  ⬛ [Run DynamoDB Local Container and ensure it works](#run-dynamodb-local-container-and-ensure-it-works)<br>
  ⬛ [Run Postgres Container and ensure it works](#run-postgres-container-and-ensure-it-works)<br>

## My Notes
### Chirag's Pricing/Spending Considerations for Week 1
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

### Ashish's Container Security Considerations for Week 1
#### Top 10 Container Security Best Practices
- practise of protecting applications hosted in containers
- Can be run in cloud or on-prem

- Container First Strategy
- Most applications are developed with Docker(Un-managed) / Managed AWS ECS / EKS
- reduces impact of breach because of application segregation
- In managed container services we just need to focus on few things - secucurity is taken care by the cloud providers
- managing container security needs practise
- Unmanaged Containers needs lots of hours / Managed there will be restrictions(deoednds on the cloud service provider)

#### Docker Compopnents
- Docker Client ---- Laptop
- Docker server(Host and Registry)Some images are public and some private
<img width="734" alt="Screenshot 2023-02-20 at 08 13 19" src="https://user-images.githubusercontent.com/15687491/220049320-fc8370ff-dcc0-4820-b434-14a3150a10bd.png">
