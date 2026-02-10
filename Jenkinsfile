pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Docker Build') {
            steps {
                sh 'docker build -t java-jenkins-demo:latest .'
            }
        }

        stage('Docker Run') {
            steps {
                sh '''
                  docker rm -f java-jenkins-demo || true
                  docker run -d --name java-jenkins-demo java-jenkins-demo:latest
                '''
            }
        }
    }

    post {
        success {
            echo 'Dockerized CI pipeline SUCCESS'
        }
        failure {
            echo 'Pipeline FAILED'
        }
    }
}