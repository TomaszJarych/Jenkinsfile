pipeline {
    agent any
    tools {
        maven 'Maven 3.6.0'
    }
    stages {
        stage ('Build'){
            steps {
                sh 'mvn clean package'
                sh "docker build -t tomcatwebapp:${env.BUILD_ID} ."
            }
        }
    }
}