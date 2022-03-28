pipeline{
    agent any
    stages{
        stage('Build ECS Cluster')
        {
            steps {
                withAWS(region:'us-east-1',credentials:'6437f700-857c-469d-acb3-b7717e09cde7')
                {
                    sh 'ecs-cli configure --cluster demo-cluster --default-launch-type EC2 --region us-east-1 --config-name demo-cluster'
                    sh 'ecs-cli up --region us-east-1 --keypair ttn-5916 --capability-iam --instance-type t2.micro --cluster-config demo-cluster --launch-type EC2 --size 2'
                    sh 'ecs-cli compose up --create-log-groups --cluster-config demo-cluster'
                    sh 'ecs-cli ps --cluster demo-cluster'
                }
            }
        }
    }
}
