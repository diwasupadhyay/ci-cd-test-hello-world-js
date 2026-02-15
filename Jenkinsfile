pipeline {
    agent any

    stages {
        stage('Build Docker Image') {
            steps {
                bat "docker build -t hello-world-app:${env.BUILD_NUMBER} ."
            }
        }

        stage('Run Container') {
            steps {
                bat 'docker stop hello-world-app || exit 0'
                bat 'docker rm hello-world-app || exit 0'
                bat "docker run -d --name hello-world-app -p 3000:3000 hello-world-app:${env.BUILD_NUMBER}"
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
