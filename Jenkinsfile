pipeline {
    agent any

    environment {
        // Define any environment variables if needed, for example, SonarQube configuration
        SONARQUBE_URL = 'http://your-sonarqube-server-url'
    }

    stages {
        stage('Checkout') {
            steps {
                // Checkout the code from GitHub
                git 'https://github.com/Nayana192003/mern-backend.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                script {
                    // Install dependencies using npm
                    sh 'npm install'
                }
            }
        }

        stage('Build') {
            steps {
                script {
                    // Run the build process (e.g., if using npm run build)
                    sh 'npm run build'
                }
            }
        }

        stage('Test') {
            steps {
                script {
                    // Run tests (e.g., npm test)
                    sh 'npm test'
                }
            }
        }

        stage('SonarQube Analysis') {
            steps {
                script {
                    // Run SonarQube analysis using SonarScanner
                    withSonarQubeEnv('SonarQube') {
                        sh 'npm run sonar'
                    }
                }
            }
        }
    }

    post {
        always {
            echo 'This will always run after the build, regardless of success or failure.'
            // You can add cleanup steps or notifications here
        }
        
        success {
            echo 'Build succeeded!'
            // You can add actions to notify success, such as sending emails or Slack messages
        }

        failure {
            echo 'Build failed!'
            // You can add actions to notify failure, such as sending emails or Slack messages
        }
    }
}
