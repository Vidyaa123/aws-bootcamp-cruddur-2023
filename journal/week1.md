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

### Create notification endpoint
Creating a notification endpoint for both frontend and backend
- open the environment in gitpod from github repo
- open openAPI-3.0.yml file - Install OpenAPI Swagger Editor if not done previously)
- Click API tab and it shows Paths for all the endpoints with example code in preview
- Startup application by right clicking docker-compose file and then click  'docker up'
- Add the code for creating a notification endpoint and view it in the preview.
``` sh
/api/activities/notifications:
    get:
      description: 'Return a feed of activity based for all of those that I follow'
      tags:
        - activities
      parameters: []
      responses:
        '200':
          description: Returns an array of activities
          content:
            application/json:
              schema:
                type: array
                items:
                  $ref: '#/components/schemas/Activity'
```

- View the endpoint in the preview
- In the backend create an endpoint in app.py file
    - create @app.route for notifications similar to home
    ```sh
    @app.route("/api/activities/notifications", methods=['GET'])
    def data_notifications():
      data = NotificationsActivities.run()
      return data, 200
    ```
- Create a new file notifications_activities.py under services
``` sh

from datetime import datetime, timedelta, timezone
class NotificationsActivities:
  def run():
    now = datetime.now(timezone.utc).astimezone()
    results = [{
      'uuid': '68f126b0-1ceb-4a33-88be-d90fa7109eee',
      'handle':  'Ikea',
      'message': 'To create a better everyday life for the many people!',
      'created_at': (now - timedelta(days=2)).isoformat(),
      'expires_at': (now + timedelta(days=5)).isoformat(),
      'likes_count': 5,
      'replies_count': 1,
      'reposts_count': 0,
      'replies': [{
        'uuid': '26e12864-1c26-5c3a-9658-97a10f8fea67',
        'reply_to_activity_uuid': '68f126b0-1ceb-4a33-88be-d90fa7109eee',
        'handle':  'Worf',
        'message': 'This post has no honor!',
        'likes_count': 0,
        'replies_count': 0,
        'reposts_count': 0,
        'created_at': (now - timedelta(days=2)).isoformat()
      }]
    }
    ]
    return results
    
```
check if the endpoint is working by clicking the url /api/activities/notifications

- creating the frontend  by modifying the app.js
```sh
import NotificationsFeedPage from './pages/NotificationsFeedPage';
```
```sh
{
    path: "/notifications",
    element: <NotificationsFeedPage />
  },
```
- add new page notificationsfeedpage
```sh
import './NotificationsFeedPage.css';
import React from "react";

import DesktopNavigation  from '../components/DesktopNavigation';
import DesktopSidebar     from '../components/DesktopSidebar';
import ActivityFeed from '../components/ActivityFeed';
import ActivityForm from '../components/ActivityForm';
import ReplyForm from '../components/ReplyForm';

// [TODO] Authenication
import Cookies from 'js-cookie'

export default function NotificationsFeedPage() {
  const [activities, setActivities] = React.useState([]);
  const [popped, setPopped] = React.useState(false);
  const [poppedReply, setPoppedReply] = React.useState(false);
  const [replyActivity, setReplyActivity] = React.useState({});
  const [user, setUser] = React.useState(null);
  const dataFetchedRef = React.useRef(false);

  const loadData = async () => {
    try {
      const backend_url = `${process.env.REACT_APP_BACKEND_URL}/api/activities/notifications`
      const res = await fetch(backend_url, {
        method: "GET"
      });
      let resJson = await res.json();
      if (res.status === 200) {
        setActivities(resJson)
      } else {
        console.log(res)
      }
    } catch (err) {
      console.log(err);
    }
  };

  const checkAuth = async () => {
    console.log('checkAuth')
    // [TODO] Authenication
    if (Cookies.get('user.logged_in')) {
      setUser({
        display_name: Cookies.get('user.name'),
        handle: Cookies.get('user.username')
      })
    }
  };

  React.useEffect(()=>{
    //prevents double call
    if (dataFetchedRef.current) return;
    dataFetchedRef.current = true;

    loadData();
    checkAuth();
  }, [])

  return (
    <article>
      <DesktopNavigation user={user} active={'notifications'} setPopped={setPopped} />
      <div className='content'>
        <ActivityForm  
          popped={popped}
          setPopped={setPopped} 
          setActivities={setActivities} 
        />
        <ReplyForm 
          activity={replyActivity} 
          popped={poppedReply} 
          setPopped={setPoppedReply} 
          setActivities={setActivities} 
          activities={activities} 
        />
        <ActivityFeed 
          title="Notifications" 
          setReplyActivity={setReplyActivity} 
          setPopped={setPoppedReply} 
          activities={activities} 
        />
      </div>
      <DesktopSidebar user={user} />
    </article>
  );
}
```

## MANDATORY CHALLENGES


### Document the Notification Endpoint for the OpenAPI Document
<img width="1087" alt="Screenshot 2023-02-21 at 18 30 27" src="https://user-images.githubusercontent.com/15687491/220707270-a08eb3b1-3c3d-4db9-81b9-fea821731654.png">

### Write a Flask Backend Endpoint for Notifications
<img width="1259" alt="Screenshot 2023-02-24 at 18 54 14" src="https://user-images.githubusercontent.com/15687491/221267279-0ae14e4e-96fb-4791-9ad1-7c31f427ca0b.png">

### Write a React Page for Notifications
<img width="1414" alt="Screenshot 2023-02-22 at 13 02 14" src="https://user-images.githubusercontent.com/15687491/220707099-bc264bba-51dd-4a64-9ec3-dc12276686b7.png">

### Run DynamoDB Local Container and ensure it works
<img width="1427" alt="Screenshot 2023-02-22 at 17 17 24" src="https://user-images.githubusercontent.com/15687491/220706819-b61ea2eb-2a7a-4c11-9109-0ee24388804e.png">

### Run Postgres Container and ensure it works
<img width="1386" alt="Screenshot 2023-02-22 at 17 12 14" src="https://user-images.githubusercontent.com/15687491/220707000-a71bbeb3-ec8d-4abe-9b14-1f749d5ff68d.png">

 
