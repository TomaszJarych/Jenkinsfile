pipeline{
    agent any
    tools {
        maven 'Maven 3.6.0'
    }
    stages{
        stage('Build'){
            steps{
                sh 'mvn clean package'
            }
            post {
                success {
                    echo 'Now archiving'
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }
        stage('Deploy to staging'){
            steps{
                copyArtifacts(upstream);
                build job: 'deploy-to-staging'
            }
        }
        stage ('Deploy to Production'){
            steps{
                timeout(time:5, unit:'DAYS'){
                    input message:'Approve PRODUCTION Deployment?'
                }

                build job: 'deploy-to-prod'
            }
            post {
                success {
                    echo 'Code deployed to Production.'
                }

                failure {
                    echo ' Deployment failed.'
                }
            }
        }
    }
}
