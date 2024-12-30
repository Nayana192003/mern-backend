pipeline {
    agent any

    environment {
        // SonarQube server configuration
        SONARQUBE_SERVER = 'SonarQube' // Name configured in Jenkins
        SONARQUBE_URL = 'http://localhost:9000/'
        SONAR_PROJECT_KEY = 'mern-backend'
    }

    stages {
        stage('Build') {
            steps {
                echo 'Building the project...'
                // Use Windows batch commands
                bat 'npm install'
            }
        }

        stage('SonarQube Analysis') {
            steps {
                echo 'Running SonarQube analysis...'
                withSonarQubeEnv("${SONARQUBE_SERVER}") {
                    bat """
                    sonar-scanner -Dsonar.projectKey=${SONAR_PROJECT_KEY} \
                                  -Dsonar.sources=./src \
                                  -Dsonar.host.url=${SONARQUBE_URL} \
                                  -Dsonar.login=<your-sonar-token>
                    """
                }
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
                echo 'Deploying project...'
                bat 'deploy_script.bat'
            }
        }
    }

    post {
        always {
            echo 'Pipeline execution complete.'
        }
        success {
            echo 'Pipeline executed successfully.'
        }
        failure {
            echo 'Pipeline failed.'
        }
    }
}
