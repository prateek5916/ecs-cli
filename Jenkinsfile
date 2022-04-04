pipeline{
    agent any
    stages{
        stage('Git Clone'){
            steps{
              //  sh 'git clone https://github.com/prateek5916/ecs-cli.git'
                sh 'cd ecs-cli/'
            }
        }
        stage('Login into ECR')
        {
            steps{
                script{
                    sh 'sudo aws ecr get-login-password --region us-east-1 |sudo docker login --username AWS --password-stdin  177635644561.dkr.ecr.us-east-1.amazonaws.com'
                }
            }
        }
        stage('Build Image')
        {
            steps{
                sh 'sudo docker build -t new-nginx-webapp .'
            }
        }
        stage('Tag & Push')
        {
            steps{
                sh 'sudo docker tag new-nginx-webapp:latest 177635644561.dkr.ecr.us-east-1.amazonaws.com/new-nginx-webapp:latest'
                sh 'sudo docker push 177635644561.dkr.ecr.us-east-1.amazonaws.com/new-nginx-webapp:latest'
            }
        }
        stage('Configure ECS Cluster')
        {
            steps{
                sh 'ecs-cli configure --cluster demo-cluster --default-launch-type EC2 --region us-east-1 --config-name demo-cluster'
            }
        }
        stage('Launch Clusters')
        {
            steps{
                sh 'ecs-cli up --region us-east-1 --keypair ttn-5916 --capability-iam --instance-type t2.micro --cluster-config demo-cluster --launch-type EC2 --size 2'
                sh 'sleep 60'
            }
        }
        stage('Create Task in Cluster')
        {
            steps{
                
                sh 'sudo octo push --replace-existing--package="ecs-cli.0.0.1.zip" --server="http://18.234.236.139:8080/" --apiKey=" API-W9OQSVL5DZDZEKYJNWJTUMW90X0XX6Q"'
              //  sh 'ecs-cli compose up --create-log-groups --cluster-config demo-cluster'
                //sh 'ecs-cli ps --cluster demo-cluster'
            }
        }
    }
}
