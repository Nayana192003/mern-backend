pipeline {
    agent any

    environment {
        // You can add environment variables here if needed
    }

    stages {
        stage('Checkout') {
            steps {
                // Checkout the code from the GitHub repository
                git branch: 'main', url: 'https://github.com/Nayana192003/mern-backend.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                script {
                    // Install the necessary dependencies using npm
                    sh 'npm install'
                }
            }
        }

        stage('Build') {
            steps {
                script {
                    // Run build command (you can adjust this if you have a build script)
                    sh 'npm run build'
                }
            }
        }

        stage('Test') {
            steps {
                script {
                    // Run tests (adjust this according to your testing setup)
                    sh 'npm test'
                }
            }
        }

        stage('SonarQube Analysis') {
            steps {
                script {
                    // Run SonarQube analysis using SonarScanner
                    sh 'sonar-scanner'
                }
            }
        }
    }

    post {
        always {
            echo 'This will always run after the build, regardless of success or failure.'
        }

        success {
            echo 'Build succeeded!'
        }

        failure {
            echo 'Build failed!'
        }
    }
}
