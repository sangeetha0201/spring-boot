pipeline {
    agent any
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
    }
}
