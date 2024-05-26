pipeline {
    agent any
    options {
        skipStagesAfterUnstable()
    }
    stages {
         stage('Clone repository') { 
            steps { 
                script{
                checkout scm
                }
            }
        }
        
        stage('Build') { 
            steps { 
                script{
                 app = docker.build("hello-world")
                }
            }
        }
        stage('Test'){
            steps {
                 echo 'Empty'
            }
        }
        stage('Push') {
            steps {
                script{
                    docker.withRegistry('https://905418152561.dkr.ecr.eu-west-1.amazonaws.com', 'ecr:eu-west-1:aws-credentials') {
                    app.push("latest")
                    }
                }
            }
        }
        stage('Deploy'){
            steps {
                 sh 'aws eks update-kubeconfig --region eu-west-1 --name task-execution-cluster'
                 sh 'kubectl apply -f deployment.yml --validate=false'
                 sh 'kubectl rollout restart deployment hello-world'
            }
        }
        
    }
}