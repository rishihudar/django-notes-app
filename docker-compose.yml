@Library("Shared") _
pipeline {
    agent { label 'vinod' }

    stages {
        
        stage("Hello"){
            steps{
                script{
                    hello()
                }
            }
        }
        
        stage('Code') {
            steps {
               script{
                clone('https://github.com/rishihudar/django-notes-app', 'main')
               }
            }
        }
        stage('Build') {
            steps {
                script{
                docker_build("notes-app","latest","rishi9759")
                }
            }
        }
        stage("Push To DockerHub"){
            steps{
                script{
                    docker_push("notes-app","latest","rishi9759")
                }
            }
        }
        stage('Deploy') {
            steps {
                echo 'This is deploying the code'
                sh 'docker compose up -d'
            }
        }
    }
}    
