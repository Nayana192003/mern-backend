pipeline {
    agent any

    tools {
        SonarQube 'SonarQube'  // Replace with the name you found
    }

    stages {
        stage('Checkout') {
            steps {
                echo 'Checking out code from GitHub repository'
                git 'https://github.com/your-repository.git'
            }
        }

        stage('SonarQube Analysis') {
            steps {
                echo 'Running SonarQube analysis...'
                withSonarQubeEnv('MySonarQube') {
                    sh 'sonar-scanner -Dsonar.projectKey=my-project -Dsonar.sources=./src -Dsonar.host.url=http://localhost:9000 -Dsonar.login=$SONAR_TOKEN'
                }
            }
        }
    }
}
