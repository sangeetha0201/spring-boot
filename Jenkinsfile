pipeline {
    agent any
    stages {
        stage('maven built'){
            steps{
                bat 'mvn clean test install'
            }
        }
        }
      post {
      always {
        junit '**/target/surefire-reports/TEST-*.xml'
      }
   } 
    }
