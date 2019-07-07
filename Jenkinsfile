pipeline {
    agent master
    stages{
        stage('Build'){
            steps {
                sh 'mvn clean package'
            }
            post {
                success {
                    echo 'Now CArchiving...'
                    archiveArtifacts artifacts: '**/target/*.war'
                }
                failure {
                    echo 'It Bloody FAILED!'
                }
            }
        }
        stage ('Deploy to Staging'){
            steps {
                build job: 'Deploy-to-staging'
            }
        }
    }
}