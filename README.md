# Launching ECS Cluster with Jenkins pipeline script 

<h1>This repository contains Jenkins pipeline script, docker-compose file for Nginx, and ECS parameters file
</h1>


REQUIREMENTS:-
    AWS Account
    EC-2 instance with Jenkins and ECS-CLI configured
    Docker compose file to launch the task or container according to requirement(Ex-Nginx webserver)
    An IAM service role or user attached with an EC2 instance running Jenkins with required permissions:-
        FullAccessEC2
        FullAccessECS
        FullAccessIAM

Setup
    AMI Setup
        Launch EC2 instance with Ubuntu or Amazon Linux AMI 
        Allow the TCP-80 port in the security group
        Install Jenkins on that instance(ref-https://www.digitalocean.com/community/tutorials/how-to-install-jenkins-on-ubuntu-20-04)
        Install ecs-cli on that instance(ref-https://docs.aws.amazon.com/AmazonECS/latest/developerguide/ECS_CLI_installation.html)
    
    Jenkins Instance Setup
        Configure the Jenkins
        Give appropriate permission to Jenkins User(Ex-sudoers permission)
        Create AWS role and attach with AMI to access AWS services

    GitHub Setup
        Set webhook to trigger the Jenkins Job
        Put the Jenkinsfile, docker-compose.yml, and ECS-params.yml file into the repository
    
    Jenkins Job Setup
        Install the required Jenkins Plugins
        Create a pipeline Job
        Add GitHub repository URL as SCM 
        Set the GitHub Poll SCM
