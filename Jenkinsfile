pipeline {
    agent any

    stages {
        // stage('VeraCode SCA Analysis') {
        //     steps {
        //         script {
        //             sh "curl -sSL https://download.sourceclear.com/ci.sh | sh | grep -o 'https://[^ ]*' | xargs -I {} sed 's#{{vc_sca_report_html}}#{}#g' report.html > temp_file && mv temp_file report.html"
        //         }
        //     }
        // }
        // stage('SonarQube Analysis') {
        //     steps {
        //         script {
        //             def mvn = tool 'Sonars';
        //             withSonarQubeEnv() {
        //                 sh "${mvn}/bin/mvn clean verify sonar:sonar -Dsonar.projectKey=Example-Java -Dsonar.projectName='Example-Java'"
        //             }
        //         }
        //     }
        // }
        stage('VeraCode SCA Analysis') {
            steps {
                script {
                    snykSecurity(
                        snykInstallation: 'snaky_demo',
                        snykTokenId: 'hts-snyk',
                        // place other parameters here
                    )
                }
            }
        }
    }

    post {
        always {
            script {
                archiveArtifacts artifacts: 'report.html', fingerprint: true
            }
        }
    }
}