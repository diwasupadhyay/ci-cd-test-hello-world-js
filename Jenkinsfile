pipeline {
    agent any

    stages {
        stage('Clone') {
            steps {
                git branch: 'main', url: 'https://github.com/YOUR_USERNAME/YOUR_REPO.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    dockerImage = docker.build("hello-world-app:${env.BUILD_NUMBER}")
                }
            }
        }

        stage('Run Container') {
            steps {
                script {
                    // Stop old container if running
                    sh 'docker stop hello-world-app || true'
                    sh 'docker rm hello-world-app || true'

                    // Run new container
                    sh "docker run -d --name hello-world-app -p 3000:3000 hello-world-app:${env.BUILD_NUMBER}"
                }
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully!'
        }
        failure {
            echo 'Pipeline failed!'
        }
    }
}
