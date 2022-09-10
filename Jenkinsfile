pipeline {
    agent any
    stages {
        stage('maven built'){
            steps{
                sh 'mvn clean install'
            }
        }
        stage('print'){
            steps{
                echo "hello "
            }
        }
            stage('compile'){
                steps{
                    sh 'pwd'
                }
            }

        }
    }
