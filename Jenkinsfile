pipeline {
    agent { label 'kube_node' }
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
                    docker.withRegistry('https://registry.hub.docker.com', 'docker-hub') {
                            myapp.push("latest")
                            myapp.push("${env.BUILD_ID}")
                    }
                }
            }
        }        
                        
}
