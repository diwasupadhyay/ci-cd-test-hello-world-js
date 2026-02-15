pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                bat 'docker build -t hello-world-app .'
            }
        }
        stage('Run') {
            steps {
                bat 'docker stop hello-world-app || exit 0'
                bat 'docker rm hello-world-app || exit 0'
                bat 'docker run -d --name hello-world-app -p 3000:3000 hello-world-app'
            }
        }
    }
}
