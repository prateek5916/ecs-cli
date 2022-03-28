# Launching ECS Cluster with Jenkins pipeline script 

<h3>This repository contains Jenkins pipeline script, docker-compose file for Nginx, and ECS parameters file
</h3>


<center><h2>REQUIREMENTS:-</center></h2>
<ul>
   <li> AWS Account</li>
    <ul>
    <li>EC-2 instance with Jenkins and ECS-CLI configured
    <li>Docker compose file to launch the task or container according to requirement(Ex-Nginx webserver)
    <li>An IAM service role or user attached with an EC2 instance running Jenkins with required permissions:-
        <ul>
        <li>FullAccessEC2
        <li>FullAccessECS
        <li>FullAccessIAM
        </ul></ul></ul>
<center><h2>Setup</center></h2>
<ul>    
<li>AMI Setup
<ul>
       <li> Launch EC2 instance with Ubuntu or Amazon Linux AMI 
        <li>Allow the TCP-80 port in the security group
        <li>Install Jenkins on that instance(ref-https://www.digitalocean.com/community/tutorials/how-to-install-jenkins-on-ubuntu-20-04)
        <li>Install ecs-cli on that instance(ref-https://docs.aws.amazon.com/AmazonECS/latest/developerguide/ECS_CLI_installation.html)
    </ul>
    <li>Jenkins Instance Setup
        <ul><li>Configure the Jenkins
        <li>Give appropriate permission to Jenkins User(Ex-sudoers permission)
        <li>Create AWS role and attach with AMI to access AWS services
</ul>
  <li> GitHub Setup
       <ul><li> Set webhook to trigger the Jenkins Job
        <li>Put the Jenkinsfile, docker-compose.yml, and ECS-params.yml file into the repository
    </ul>
   <li> Jenkins Job Setup
       <ul><li> Install the required Jenkins Plugins
        <li>Create a pipeline Job
        <li>Add GitHub repository URL as SCM 
        <li>Set the GitHub Poll SCM
</ul>
</ul>
