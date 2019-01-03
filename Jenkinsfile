pipeline{
    agent any
    tools {
        maven 'Maven 3.6.0'
    }
    stages{
        stage('Build'){
            steps{
                sh 'mvn clean compile'
            }
            post {
                success {
                    echo 'Now archiving'
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }
    }
}