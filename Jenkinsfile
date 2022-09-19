pipeline {
    agent any
    stages {
        stage('SonarQube analysis') {
            when { allOf { environment name: 'OS-Type', value: 'windows'} }
            steps {
                withSonarQubeEnv('local-sonar1') {
                   bat 'mvn clean org.jacoco:jacoco-maven-plugin:prepare-agent install org.jacoco:jacoco-maven-plugin:report'
                   bat 'mvn sonar:sonar' 
                }
            }
        }
        stage("Quality Gate") {
            when { allOf { environment name: 'OS-Type', value: 'windows'} }
            steps {
                sleep(60)
                timeout(time: 5, unit: 'MINUTES') {
                    // Parameter indicates whether to set pipeline to UNSTABLE if Quality Gate fails
                    // true = set pipeline to UNSTABLE, false = don't
                    waitForQualityGate abortPipeline: true
                }
            }
        }
        stage('maven  windows build'){
            when { allOf { environment name: 'OS-Type', value: 'windows'} }
            steps{
                bat 'mvn clean install -Dbuid.number=%BUILD_NUMBER%'
            }
        }
        stage('maven  linux build'){
            when { allOf { environment name: 'OS-Type', value: 'linux'} }
            steps{
                sh 'mvn clean install -Dbuid.number=%BUILD_NUMBER%'
            }
        }
        }
      post {
      always {
        junit '**/target/surefire-reports/TEST-*.xml'
      }
   } 
    }
