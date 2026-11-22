pipeline {
    agent any

    stages {

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t html-demo-app .'
            }
        }

        stage('Deploy Application') {
            steps {
                sh '''
                    docker stop html-app || true
                    docker rm html-app || true

                    docker run -d \
                    --name html-app \
                    -p 80:80 \
                    html-demo-app
                '''
            }
        }
    }

    post {
        success {
            echo 'Application deployed successfully!'
        }

        failure {
            echo 'Deployment failed!'
        }
    }
}
