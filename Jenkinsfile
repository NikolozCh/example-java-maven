pipeline {
    agent any

    stages {
        stage('VeraCode SCA Analysis') {
            steps {
                script {
                    sh "curl -sSL https://download.sourceclear.com/ci.sh | sh"
                }
            }
        }
        stage('SonarQube Analysis') {
            steps {
                script {
                    def mvn = tool 'Sonars';
                    withSonarQubeEnv() {
                        sh "${mvn}/bin/mvn clean verify sonar:sonar -Dsonar.projectKey=Example-Java -Dsonar.projectName='Example-Java'"
                    }
                }
            }
        }
    }
}