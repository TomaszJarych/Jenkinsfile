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
                build job: 'deploy-to-staging'
            }

        }
    }
}
