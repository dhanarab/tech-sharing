pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building..'
                sh 'echo ABC > result.txt'
                archiveArtifacts artifacts: 'result.txt', fingerprint: true
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Deploy') {
            when {
              expression {
                return (sh(script:"false", returnStatus: true) == 0)
              }
            }
            steps {
                echo 'Deploying....'
            }
        }
    }
}
