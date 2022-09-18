pipeline {
    agent any
    stages {
        
        stage('mMven build'){
            steps{
                sh 'mvn clean install -Dbuid.number=%BUILD_NUMBER%'
            }
        }
        }

    }
