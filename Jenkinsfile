pipeline {
    agent any

    environment {
        // Set SonarQube server name (configured in Jenkins)
        SONARQUBE_SERVER = 'SonarQube' // This is the name you gave the server in Jenkins config
    }

    stages {
        stage('Build') {
            steps {
                echo 'Building the project...'
                // Use Windows batch commands instead of Unix shell
                bat 'npm install'  // for Windows
            }
        }

        stage('SonarQube Analysis') {
            steps {
                echo 'Running SonarQube analysis...'
                script {
                    // Run SonarQube analysis
                    sonarScanner(
                        installationName: "${SONARQUBE_SERVER}",
                        options: [
                            '-Dsonar.projectKey=your_project_key',
                            '-Dsonar.sources=./src',
                            '-Dsonar.host.url=http://your_sonarqube_server'
                        ]
                    )
                }
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests...'
                bat 'npm test'  // for Windows
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying project...'
                // Add your deploy commands here, use bat for Windows
                bat 'deploy_script.bat'
            }
        }
    }
}
