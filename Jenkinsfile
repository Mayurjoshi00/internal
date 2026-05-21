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
                    sh 'docker build -t myapp -f ../Dockerfile .'

                }
            }
        }

        stage('Run Container') {
            steps {
                sh 'docker stop myapp || true'
                sh 'docker rm myapp || true'
                sh 'docker run -d -p 3000:3000 --name myapp myapp'
            }
        }
    }
}
