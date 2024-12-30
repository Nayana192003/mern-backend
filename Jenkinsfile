pipeline {
    agent any
    environment {
        SONARQUBE = 'SonarQube'  // Name of the SonarQube server you configured in Jenkins
    }
    stages {
        stage('Checkout') {
            steps {
                // Checkout the code from GitHub repository
                git 'https://github.com/your-repository.git'
            }
        }
        stage('Install Dependencies') {
            steps {
                // Install dependencies (for Node.js project)
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
                        -Dsonar.projectKey=your_project_key \
                        -Dsonar.sources=./src \
                        -Dsonar.host.url=http://localhost:9000 \
                        -Dsonar.login=your_sonarqube_token
                    """
                }
            }
        }
        stage('Build') {
            steps {
                // Run your build commands here (e.g., npm build for Node.js)
                sh 'npm run build'
            }
        }
    }
    post {
        always {
            // Clean up actions, like archiving artifacts, etc.
        }
    }
}
