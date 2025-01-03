pipeline {
    agent any
    environment {
        SONARQUBE = 'SonarQube'  // Name of the SonarQube server you configured in Jenkins
        SONARQUBE_TOKEN = 'sqp_3c91dd70eef0be4404743cb3d90a17b7ade3f030' // Replace with your actual token
        SONARQUBE_URL = 'http://localhost:9000' // Replace with your SonarQube server URL
        SONAR_PROJECT_KEY = 'mern-backend' // Replace with your actual SonarQube project key
    }
    stages {
        stage('Checkout') {
            steps {
                // Checkout the code from GitHub repository, specify the branch
                git branch: 'main', url: 'https://github.com/Nayana192003/mern-backend.git'  // Replace with your GitHub repo URL
            }
        }
        stage('Install Dependencies') {
            steps {
                // Install dependencies for a Node.js project
                sh 'npm install'
            }
        }
        stage('SonarQube Analysis') {
            steps {
                // Run SonarQube analysis
                script {
                    // Trigger SonarQube analysis using SonarScanner
                    sh """
                        sonar-scanner \
                        -Dsonar.projectKey=${SONAR_PROJECT_KEY} \
                        -Dsonar.sources=./src \
                        -Dsonar.host.url=${SONARQUBE_URL} \
                        -Dsonar.login=${SONARQUBE_TOKEN}
                    """
                }
            }
        }
        stage('Build') {
            steps {
                // Run your build commands (e.g., npm run build for Node.js)
                sh 'npm run build'
            }
        }
    }
    post {
        always {
            // Clean up actions, like archiving artifacts, etc.
            echo 'Build and SonarQube analysis complete.'
        }
    }
}
