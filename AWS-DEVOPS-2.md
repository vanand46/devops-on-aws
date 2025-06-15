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

**Github.com** -> **Code Build** -> **Beanstalk**

**Note** - Beanstalk is a service offered by AWS where the complete infra like ec2 instances, load balancer, autoscaling, security managed by AWS.
