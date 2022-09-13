pipeline {
    agent any
    stages {
        stage('SonarQube analysis') {
            steps {
                withSonarQubeEnv('local-sonar1') {
                   bat 'mvn clean org.jacoco:jacoco-maven-plugin:prepare-agent install org.jacoco:jacoco-maven-plugin:report'
                    bat 'mvn sonar:sonar -Dsonar.branch.name=%BRANCH_NAME%' 
                }
            }
        }
        stage("Quality Gate") {
            steps {
                sleep(60)
                timeout(time: 5, unit: 'MINUTES') {
                    // Parameter indicates whether to set pipeline to UNSTABLE if Quality Gate fails
                    // true = set pipeline to UNSTABLE, false = don't
                    waitForQualityGate abortPipeline: true
                }
            }
        }
        stage('mMven build'){
            steps{
                bat 'mvn clean install -Dbuid.number=%BUILD_NUMBER%'
            }
        }
        }
      post {
      always {
        junit '**/target/surefire-reports/TEST-*.xml'
      }
   } 
    }
