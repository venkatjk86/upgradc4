pipeline{
    agent any
     stages {
        stage('Git Checkout') {
          steps {
            echo "Checkout"
            checkout scm
          }
        }
        stage('Building Docker Image'){
            steps{
                echo 'Testing'
                sh 'docker --version'
            }
        }
        stage('Deploy'){
            steps{
		        sh "eval \$(aws ecr-public get-login-password --region us-east-1 | docker login --username AWS --password-stdin public.ecr.aws/g3c7k1t7) && sleep 2"
                sh "docker build . -t upgrad-app-karthickeyan-assignment"
                sh "docker push public.ecr.aws/g3c7k1t7/upgrad-app-karthickeyan-assignment:latest"
            }
        }
     }
}
