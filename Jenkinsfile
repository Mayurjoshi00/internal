pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build Demo Image') {
            steps {
                dir('myapp') {
                    sh 'docker build -t myapp:demo .'
                }
            }
        }

        stage('Run Container') {
            steps {
                // Stops any running container from a previous build and starts a new one
                sh 'docker stop myapp-demo || true'
                sh 'docker rm myapp-demo || true'
                sh 'docker run -d -p 3000:3000 --name myapp-demo myapp:demo'
            }
        }
    }
}
