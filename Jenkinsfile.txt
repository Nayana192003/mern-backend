pipeline {
    agent any
    
    stages {
        stage('Build') {
            steps {
                echo 'Building the project...'
                // Add commands to build your project (e.g., npm install or npm run build)
            }
        }
        stage('Test') {
            steps {
                echo 'Running tests...'
                // Add commands to run tests (e.g., npm test)
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying project...'
                // Add commands to deploy your project
            }
        }
    }
}
