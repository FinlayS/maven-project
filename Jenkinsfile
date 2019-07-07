pipeline {
    agent any
    stages{
        stage('Build'){
            steps {
                sh 'maven clean package'
            }
            post {
                success {
                    echo 'Now CArchiving...'
                    archiveArtifacts artifacts: '**/target/*.war'
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