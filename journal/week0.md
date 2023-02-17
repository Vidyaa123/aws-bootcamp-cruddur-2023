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
  :white_check_mark: [Pricing Quiz](#pricing-quiz)<br>
  :white_check_mark: [Security Quiz](#security-quiz)<br><br>
  
- [**BROWNIE CHALLENGES**](#brownie-challenges)<br>
  :black_square_button: [Destroy your root account credentials, Set MFA, IAM role](#destroy-your-root-account-credentials-set-mfa-iam-role)<br>
  :black_square_button: [Use EventBridge to hookup Health Dashboard to SNS and send notification when there is a service health issue.](#use-eventbridge-to-hookup-health-dashboard-to-sns-and-send-notification-when-there-is-a-service-health-issue)<br>
  :black_square_button: [Review all the questions of each pillars in the Well Architected Tool (No specialized lens)](#review-all-the-questions-of-each-pillars-in-the-well-architected-tool-no-specialized-lens)<br>
  :black_square_button: [Create an architectural diagram (to the best of your ability) the CI/CD logical pipeline in Lucid Charts](#create-an-architectural-diagram-to-the-best-of-your-ability-the-cicd-logical-pipeline-in-lucid-charts)<br>
  :black_square_button: [Research the technical and service limits of specific services and how they could impact the technical path for technical flexibility.](#research-the-technical-and-service-limits-of-specific-services-and-how-they-could-impact-the-technical-path-for-technical-flexibility)<br>
  :black_square_button: [Open a support ticket and request a service limit](#open-a-support-ticket-and-request-a-service-limit)<br>
<br>

## My Notes
####Ephemeral Microblogging platform

Investers - Cost/Budget

Web Dev Group

CTO

iron triangle - Fast-cheap-good

####Architecture:

Requirements/Risks/Assumptions/Constraints**

- requirements

Common dictionary between all people

requirements - project that must be achieved at the end

it should be measurable

feasible/monitorable/traceable/verifiable

- risks

that prevents the project from being successful

single point of failure

Late delivery

- assumptions

factors held as true for the planning and implementation phase

example - budget is approved, enough network bandwidth

- constraints

policy or technical limitations for the project

time/budget/vendor selection

£0 using free tier/14-16 weeks/


#### Initial Conceptual design - HLD

understandable by business stakeholders -*napkin design*

organises and defines concepts and rules

#### Logical design

defines how the system should be implemented

Blueprint

break large conceptual block to more logical blocks

#### physical design - LLD

representing the actual thing that is build

down to individual description

#### TOGAF - architecture framework

maps closely to WAF

C4 model for visualising software architecture
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

### Generating AWS Credentials
Created access credentials for IAM user. This credential can be used to access AWS CLI.


### Install AWS CLI
Installed AWS ClI in Gitpod. Instead of running the install everytime the script was added to gitpod.yml file so it gets automatically executed when a new workspace is created.

### Create a Billing Alarm
<img width="1440" alt="Screenshot 2023-02-16 at 07 56 17" src="https://user-images.githubusercontent.com/15687491/219302984-a1b82c84-cc96-46e9-8734-ed6af32f21be.png">

### Create a AWS Budget
<img width="1440" alt="Screenshot 2023-02-15 at 19 33 41" src="https://user-images.githubusercontent.com/15687491/219291053-f54cdf69-434f-4f71-8819-152c6b16838d.png">
