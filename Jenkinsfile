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
                return (sh(script:"true", returnStatus: true) == 0)
              }
            }
            steps {
                echo 'Deploying....'
            }
        }
    }
}
