# AWS DevOps - CI/CD Pipeline in AWS

## Code Pipeline

- Fully managed CI/CD by AWS.
- Automates the process of building, testing, and deploying the code everytime there is a change.
- No severs to manage
- Fully integrated AWS services
- Continuous Delivery.End to End software release.
- Integration with third party tools: Works with GitHub, Jenkins, SonarQube etc.

## Build Tools - AWS Code Build (alternative to maven)

- Service that compiles source code, run tests, and produces software packages that are already ready to be deployed.
- Eliminates the need to provision, manage and scale your own build servers.
- Costly tool.
- Fully managed.

## Code Pipeline An Example

It is the step by step process via which we can automate the project deployment.

**Github.com** -> **Code Build** -> **Beanstalk**

**Note** - Beanstalk is a service offered by AWS where the complete infra like ec2 instances, load balancer, autoscaling, security managed by AWS.

### Create the pipeline

- Go to AWS Console and search for CodePipline
![alt text](image-31.png)

- Click on 'Create Pipepline' and select 'Build custom pipline' then click 'Next'
![alt text](image-32.png)

- On this window, Give a Pipeline name, then select 'Superseded' as Execution mode.
- Then select 'New service role' as Service role, then please provide role service name, then click next.
![alt text](image-33.png)

- Open the following link in another tab or window of the browser.
    - https://github.com/akshu20791/apachewebsite

- Click on fork button
![alt text](image-34.png)

- Go back to your code pipeline creation window and select the 'GitHub(via OAuth app)' from source provider list.
![alt text](image-35.png)

- Click on connect
  - There connect your github account with the aws code pipeline
![alt text](image-36.png)
![alt text](image-37.png)

- Then select repo forked above from the repositries list and select master as the branch, then click next.
![alt text](image-38.png)

- Skip the build page and skip test page
![alt text](image-39.png)

- Then from the Deploy provide list select, AWS Elastic Beanstalk

### Lets deploy the sample php application on elastic beanstalk
![alt text](image-40.png)
![alt text](image-41.png)
![alt text](image-42.png)
![alt text](image-43.png)
![alt text](image-44.png)
![alt text](image-45.png)

- Then Press Next
- In front of Service role -> Create role
    - Next -> next -> create role
        ![alt text](image-46.png)
        ![alt text](image-47.png)
- Go back to elastic beanstalk -> check the role\
![alt text](image-48.png) 
- Similarly create role for ec2 instance
    - Create role -> next -> next -> next
        ![alt text](image-49.png)
![alt text](image-50.png)
- To generate the key pair -> go to ec2 -> create a new keypair
![alt text](image-51.png) 
![alt text](image-52.png)
- In Elasticbeanstalk, select the created key pair
![alt text](image-53.png)

- Click Next
- Select vpc from drop down and check the 'Public IP address' as activated
![alt text](image-54.png)
![alt text](image-55.png)
- Click Next
- In Root volume type: general purpose 3 (ssd) and then press Next
![alt text](image-56.png)
- Next -> Create
![alt text](image-57.png)

### Now lets move back to code pipeline and we will deploy the code to the elastic beanstalk
![alt text](image-58.png)
- Create Pipeline
![alt text](image-59.png)
![alt text](image-60.png)

**Deployment WILL FAIL**
Lets solve the issue:
If the Deployment fails this is because the IAM role does not have elastic beanstalk
full permission. Select code pipeline and check the role attached to it…and now go to
iam and search for the role and attach that specific role

- Click on deploy box on deploy button
![alt text](image-61.png)
- Settings -> click on service role ARN
![alt text](image-62.png)
- Add Policies
![alt text](image-63.png)
![alt text](image-64.png)
- Add Permissions
- Add retry the failed stage in pipeline
![alt text](image-65.png)
![alt text](image-66.png)
- Now lets go and check the environment endpoint url for beanstalk
![alt text](image-67.png)
![alt text](image-68.png)
