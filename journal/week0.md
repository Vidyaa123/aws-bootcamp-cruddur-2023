# Week 0 — Billing and Architecture :cloud:

## Tasks to Complete
- [**MY NOTES**](#my-notes)<br>
- [**MANDATORY CHALLENGES**](#mandatory-challenges)<br>
  :white_check_mark: [Recreate Conceptual Diagram in Lucid Chart or Napkin](#recreate-conceptual-diagram-in-lucid-chart-or-napkin)<br>
  :white_check_mark: [Recreate Logical Architectural Diagram in Lucid Chart](#recreate-logical-architectural-diagram-in-lucid-chart)<br>
  :white_check_mark: [Create an Admin User](#create-an-admin-user)<br>
  :white_check_mark: [Using CloudShell](#using-cloudshell)<br>
  :white_check_mark: [Generating AWS Credentials](#generating-aws-credentials)<br>
  :white_check_mark: [Install AWS CLI](#install-aws-cli)<br>
  :white_check_mark: [Create a Billing Alarm](#create-a-billing-alarm)<br>
  :white_check_mark: [Create a AWS Budget](#create-a-aws-budget)<br><br>
  
- [**QUIZ**](#quiz)<br>
  :white_check_mark: [Pricing & Security Quiz](#pricing-&-security-quiz)<br><br>
 
  
- [**BROWNIE CHALLENGES**](#brownie-challenges)<br>
  :white_check_mark: [Destroy your root account credentials, Set MFA, IAM role](#destroy-your-root-account-credentials-set-mfa-iam-role)<br>
  :black_square_button: [Use EventBridge to hookup Health Dashboard to SNS and send notification when there is a service health issue.](#use-eventbridge-to-hookup-health-dashboard-to-sns-and-send-notification-when-there-is-a-service-health-issue)<br>
  :black_square_button: [Review all the questions of each pillars in the Well Architected Tool (No specialized lens)](#review-all-the-questions-of-each-pillars-in-the-well-architected-tool-no-specialized-lens)<br>
  :black_square_button: [Create an architectural diagram (to the best of your ability) the CI/CD logical pipeline in Lucid Charts](#create-an-architectural-diagram-to-the-best-of-your-ability-the-cicd-logical-pipeline-in-lucid-charts)<br>
  :black_square_button: [Research the technical and service limits of specific services and how they could impact the technical path for technical flexibility.](#research-the-technical-and-service-limits-of-specific-services-and-how-they-could-impact-the-technical-path-for-technical-flexibility)<br>
  :black_square_button: [Open a support ticket and request a service limit](#open-a-support-ticket-and-request-a-service-limit)<br><br>

## My Notes
#### Ephemeral Micro-blogging platform

- Me - Cloud Engineer
- Investers - Cost/Budget
- Web Dev Group
- Fractional CTO

iron triangle - Fast-cheap-good

The frontend application is written in Javascript using react and backend application should be written in Python using Flask
Should take advantage of microserverice architecture

#### Architecture:

Requirements/Risks/Assumptions/Constraints

- requirements

    - Common dictionary between all people

    - requirements - project that must be achieved at the end

    - it should be measurable

    - feasible/monitorable/traceable/verifiable

- risks

    - that prevents the project from being successful

    - single point of failure

    - Late delivery

- assumptions

    - factors held as true for the planning and implementation phase

    - example - budget is approved, enough network bandwidth

- constraints

    - policy or technical limitations for the project

    - time/budget/vendor selection

    - £0 using free tier/14-16 weeks/


#### Initial Conceptual design - HLD

- understandable by business stakeholders - napkin design*

- organises and defines concepts and rules

#### Logical design

- defines how the system should be implemented 

- Blueprint

- break large conceptual block to more logical blocks

#### physical design - LLD

- representing the actual thing that is build

- down to individual description

#### TOGAF - architecture framework

maps closely to WAF

C4 model for visualising software architecture

### Install AWS CLI

- install the AWS CLI in Gitpod workspace

- Set AWS CLI to use partial auto-prompt mode (easier to debug CLI commands

- Update `.gitpod.yml` to include the following task

```sh
tasks:
  - name: aws-cli
    env:
      AWS_CLI_AUTO_PROMPT: on-partial
    init: |
      cd /workspace
      curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
      unzip awscliv2.zip
      sudo ./aws/install
      cd $THEIA_WORKSPACE_ROOT
```

### Set Environment Variables

It can be set in bash terminal or make Gitpod remember these credentials on relaunch
```
export AWS_ACCESS_KEY_ID=""
export AWS_SECRET_ACCESS_KEY=""
export AWS_DEFAULT_REGION=eu-west-2
```

```
gp env AWS_ACCESS_KEY_ID=""
gp env AWS_SECRET_ACCESS_KEY=""
gp env AWS_DEFAULT_REGION=eu-west-2
```

### Command to check aws cli to get user identity

```sh
aws sts get-caller-identity
```
## Mandatory Challenges
### Recreate Conceptual Diagram in Lucid Chart or Napkin
#### I recreated the conceptual diagram from the bootcamp using Lucid Chart. First time, using this tool and it was a breeze to work with. I am able to understand on a high level what are the features and services that we will be using and how they are connected.
![Cruddur - Conceptual Diagram](https://user-images.githubusercontent.com/15687491/219129797-b89582e1-d19b-4b92-afb7-ab610f15e949.png)
[*Click to View Conceptual diagram in Lucid Chart*](https://lucid.app/lucidchart/83d84872-141a-4d0e-b5c5-4b95d35a2320/edit?viewport_loc=-8%2C-179%2C1579%2C911%2C0_0&invitationId=inv_d891e448-a1b3-4b03-874b-efb145ce5920)

### Recreate Logical Architectural Diagram in Lucid Chart
#### Recreated the logical diagram created by Andrew,
Logical diagram helped me to understand the individual AWS services that will be used in this project. 
![Logical Architectural Diagram - Cruddur](https://user-images.githubusercontent.com/15687491/219449948-db3d502f-df72-4471-a62f-51fba83a786a.png)
[*Click to View Logical Architectural diagram in Lucid Chart*](https://lucid.app/lucidchart/21671dd3-755a-4205-8cbd-2a08591d8836/edit?viewport_loc=-688%2C-822%2C3787%2C2167%2C0_0&invitationId=inv_3b593746-e813-4730-83bb-d746515cf59f)

### Create an Admin User 
I created a user and added it to Admin group which has all Administrative privileges attached to it. So all users in the group will inherit those privileges. By default an IAM user does not have any access.(Prinicple of least Privilege)

<img width="1391" alt="Screenshot 2023-02-16 at 12 00 21" src="https://user-images.githubusercontent.com/15687491/219359580-638dda70-2994-4e29-9d86-ab38db9b2eff.png">

### Using CloudShell
Used Cloudshell to try out various CLI commands.
<img width="1436" alt="Screenshot 2023-02-17 at 15 32 10" src="https://user-images.githubusercontent.com/15687491/219697497-83706624-8265-402d-93e2-9bc93e6d71b8.png">

### Generating AWS Credentials
Created access credentials for IAM user. This credential can be used to access AWS CLI.

![Screenshot 2023-02-17 at 15 33 35](https://user-images.githubusercontent.com/15687491/219699849-4a9bc0f2-8142-45d0-811d-70fa67e9a4f5.jpg)

### Install AWS CLI
Installed AWS ClI in Gitpod. Instead of running the install everytime the script was added to gitpod.yml file so it gets automatically executed when a new workspace is created.
<img width="1419" alt="Screenshot 2023-02-17 at 15 29 08" src="https://user-images.githubusercontent.com/15687491/219696497-c9a05185-90dc-4610-9925-3d70ae9a5cb9.png">

### Create a Billing Alarm

- Root Account under billing and `Billing Preferences` Choose `Receive Billing Alerts`

### Create SNS Topic

- Create an SNS topic 
- The SNS topic will deliver an alert when the bill exceeds the limit

Create a SNS Topic
```sh
aws sns create-topic --name billing-alarm
```
Create a subscription supply the TopicARN and Email
```sh
aws sns subscribe \
    --topic-arn TopicARN \
    --protocol email \
    --notification-endpoint your@email.com
```
Check email to confirm the subscription

#### Create Alarm

- Update the configuration json script with the TopicARN 

```sh
aws cloudwatch put-metric-alarm --cli-input-json file://aws/json/alarm_config.json
```

<img width="1440" alt="Screenshot 2023-02-16 at 07 56 17" src="https://user-images.githubusercontent.com/15687491/219302984-a1b82c84-cc96-46e9-8734-ed6af32f21be.png">

### Create a AWS Budget

<img width="1440" alt="Screenshot 2023-02-15 at 19 33 41" src="https://user-images.githubusercontent.com/15687491/219291053-f54cdf69-434f-4f71-8819-152c6b16838d.png">


## Quiz
### Pricing & Security Quiz 
<img width="1112" alt="Screenshot 2023-02-17 at 15 55 08" src="https://user-images.githubusercontent.com/15687491/219702346-b5b2496e-1cff-47b5-89d5-39955d32b16d.png">

