pipeline {
    agent any

    tools {
        maven 'Maven 3.8.8' // Make sure this matches the name configured in Jenkins Global Tools
        jdk 'JDK 17'         // Or whatever version your project uses
    }

    environment {
        // Set environment variables if needed
    }

    stages {
        stage('Checkout') {
            steps {
                echo 'Cloning the repository...'
                checkout scm
            }
        }

        stage('Build') {
            steps {
                echo 'Building the project using Maven...'
                sh 'mvn clean package'
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests...'
                sh 'mvn test'
            }
        }

        stage('Deploy (Local Run)') {
            steps {
                echo 'Running the Spring Boot application'
                sh 'nohup java -jar target/*.jar &'
            }
        }
    }

    post {
        always {
            echo 'Pipeline finished.'
        }
        success {
            echo 'Build succeeded!'
        }
        failure {
            echo 'Build failed.'
        }
    }
}
