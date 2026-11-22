pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                git 'https://github.com/UdayPratapKourav/html-demo-apk.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t html-demo-app .'
            }
        }

        stage('Deploy') {
            steps {
                sh '''
                    docker stop html-app || true
                    docker rm html-app || true
                    docker run -d --name html-app -p 80:80 html-demo-app
                '''
            }
        }
    }
}
