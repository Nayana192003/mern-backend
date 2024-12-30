pipeline {
    agent any

    environment {
        SONAR_HOST_URL = 'http://localhost:9000' // Your SonarQube server URL
    }

    stages {
        stage('Checkout') {
            steps {
                echo 'Checking out source code...'
                checkout scm
            }
        }

        stage('Build') {
            steps {
                echo 'Building the project...'
                bat 'npm install'
            }
        }

        stage('SonarQube Analysis') {
            environment {
                // Fetch the SonarQube token securely from Jenkins credentials
                SONAR_TOKEN = credentials('SonarQubeToken') // Use the ID you gave when adding the token to Jenkins
            }
            steps {
                echo 'Running SonarQube analysis...'
                bat """
                sonar-scanner -Dsonar.projectKey=mern-backend ^
                              -Dsonar.sources=./src ^
                              -Dsonar.host.url=$SONAR_HOST_URL ^
                              -Dsonar.login=$SONAR_TOKEN
                """
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests...'
                bat 'npm test'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying the application...'
                // Add deployment steps here
            }
        }
    }

    post {
        success {
            echo 'Pipeline executed successfully!'
        }
        failure {
            echo 'Pipeline failed.'
        }
    }
}
