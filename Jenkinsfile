pipeline {
    agent any
    stages {
        stage('SonarQube analysis') {
            steps {
                withSonarQubeEnv('local-sonarqube') {
                   bat 'mvn clean org.jacoco:jacoco-maven-plugin:prepare-agent install org.jacoco:jacoco-maven-plugin:report'
                   bat 'mvn sonar:sonar' 
                }
            }
        }
        stage('maven build'){
            steps{
                bat 'mvn clean install'
            }
        }
        }
      post {
      always {
        junit '**/target/surefire-reports/TEST-*.xml'
      }
   } 
    }
