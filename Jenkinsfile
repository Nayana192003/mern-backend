pipeline {
    agent any

    environment {
        // Define the path to the Node.js installation configured in Jenkins
        NODE_HOME = tool name: 'NodeJS', type: 'NodeJS'
        PATH = "${NODE_HOME}/bin:${env.PATH}"
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
                // Install dependencies using npm
                script {
                    sh 'npm install'
                }
            }
        }

        stage('Build') {
            steps {
                // Build the project (if required, or you can skip this step if not needed)
                script {
                    sh 'npm run build'
                }
            }
        }

        stage('Test') {
            steps {
                // Run tests (if you have a test script in your package.json)
                script {
                    sh 'npm test'
                }
            }
        }

        stage('SonarQube Analysis') {
            steps {
                // Trigger SonarQube analysis
                script {
                    // Run SonarQube analysis using the SonarScanner
                    sh 'npm run sonar'
                }
            }
        }
    }

    post {
        always {
            // Actions to be performed after the pipeline completes, regardless of success or failure
            echo 'This will always run after the build, regardless of success or failure.'
        }
        success {
            // Actions to perform if the build was successful
            echo 'Build and analysis were successful!'
        }
        failure {
            // Actions to perform if the build failed
            echo 'Build failed!'
        }
    }
}
