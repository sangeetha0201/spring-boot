pipeline {
    agent { label 'ubuntuslave-1' }
    stages {
        stage('maven built'){
            steps{
                sh 'mvn clean install package'
            }
        }
        stage('print'){
            steps{
                echo "welcome "
            }
        }
            stage('compile'){
                steps{
                    sh 'pwd'
                }
            }

        }
    }
