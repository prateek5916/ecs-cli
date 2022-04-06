pipeline{
    agent any
     environment{
            bn = currentBuild.number
    }
    stages{
        stage('Git Clone'){
            steps{
                sh 'rm -rf ecs-cli'
              sh 'git clone https://github.com/prateek5916/ecs-cli.git'
                //sh 'cd ecs-cli/'
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
        stage('Making Zip for Pushing')
        {
            steps{
               sh  'zip -r lastfinal.0.0.${buildNumber}.zip *'
            }
            
        }
       stage('Deploying on Octopus')
         {
             steps{
                
                 sh 'octo push --replace-existing --package="lastfinal.0.0.${bn}.zip" --server="http://23.22.67.208:8080/" --apiKey="API-W9OQSVL5DZDZEKYJNWJTUMW90X0XX6Q"'
               
             }
         }
    }
}
