pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                echo 'Cloning repository'
                checkout scm
            }
        }

        stage('Build') {
            steps {
                echo 'Building Java application'
                sh 'mvn clean package'
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests'
                sh 'mvn test'
            }
        }
    }

    post {
        success {
            echo 'Build completed successfully'
        }
        failure {
            echo 'Build failed'
        }
    }
}
