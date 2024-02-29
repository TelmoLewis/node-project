pipeline {
    agent any
 
    stages {
         stage('Init') {
            steps {
                sh 'docker rm -f $(docker ps -qa) || true'
                  sh 'docker network create new-network || true'
            }
        }
        stage('Build') {
            steps {
                sh 'docker build -t node-app .'
                
            }
        }
 
        stage('Deploy') {
            steps {
                sh 'docker run -d -p 80:5000 --name node-app --network new-network node-app'
                
            }
        }
    }
}
