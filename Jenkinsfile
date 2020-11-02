pipeline {
    agent any
    stages {
        stage("Checkout code") {
            steps {
                git branch: 'master', url: 'https://github.com/Deepak-Khandelwal/Nginx-Docker.git'
            }
        }
        stage("Build image") {
            steps {
                script {
                    myapp = docker.build("deepakkhandelwal/nginx-web-app:${env.BUILD_ID}")
                }
            }
        }
        stage("Push image") {
            steps {
                script {
                    docker.withRegistry('', 'docker-hub') {
                            myapp.push()
                    }
                }
            }
        }        
    }                   
}
