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
		        sh "eval \$(aws ecr get-login-password --region us-east-1 | docker login --username AWS --password-stdin 915501983696.dkr.ecr.us-east-1.amazonaws.com) && sleep 2"
                sh "docker build -t venkatc4assgnmnt ."
                sh "docker push 915501983696.dkr.ecr.us-east-1.amazonaws.com/venkatc4assgnmnt:latest"
            }
        }
     }
}
