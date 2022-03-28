pipeline{
    agent any

    stages{
        stage('Creating Profile for ECS')
        {
            steps {
                sh 'ecs-cli configure --cluster demo-cluster --default-launch-type EC2 --region us-east-1 --config-name demo-cluster'
//                 sh 'ecs-cli up --region us-east-1 --keypair ttn-5916 --capability-iam --instance-type t2.micro --cluster-config demo-cluster --launch-type EC2 --size 2'
//                 sh 'ecs-cli compose up --create-log-groups --cluster-config demo-cluster'
//                 sh 'ecs-cli ps --cluster demo-cluster'
            }
        }
        stage('Build ECS Cluster')
        {
            steps {
                //sh 'ecs-cli configure --cluster demo-cluster --default-launch-type EC2 --region us-east-1 --config-name demo-cluster'
                sh 'ecs-cli up --region us-east-1 --keypair ttn-5916 --capability-iam --instance-type t2.micro --cluster-config demo-cluster --launch-type EC2 --size 2'
//                 sh 'ecs-cli compose up --create-log-groups --cluster-config demo-cluster'
//                 sh 'ecs-cli ps --cluster demo-cluster'
            }
        }
        stage('Creating a task  in ECS')
        {
            steps {
//                 sh 'ecs-cli configure --cluster demo-cluster --default-launch-type EC2 --region us-east-1 --config-name demo-cluster'
//                 sh 'ecs-cli up --region us-east-1 --keypair ttn-5916 --capability-iam --instance-type t2.micro --cluster-config demo-cluster --launch-type EC2 --size 2'
                sh 'ecs-cli compose up --create-log-groups --cluster-config demo-cluster'
         //       sh 'ecs-cli ps --cluster demo-cluster'
            }
        }
        stage('Checking Status')
        {
            steps {
//                 sh 'ecs-cli configure --cluster demo-cluster --default-launch-type EC2 --region us-east-1 --config-name demo-cluster'
//                 sh 'ecs-cli up --region us-east-1 --keypair ttn-5916 --capability-iam --instance-type t2.micro --cluster-config demo-cluster --launch-type EC2 --size 2'
//                 sh 'ecs-cli compose up --create-log-groups --cluster-config demo-cluster'
                sh 'ecs-cli ps --cluster demo-cluster'
            }
        }
        
    }
}
