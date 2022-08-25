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
                echo "Running ${env.BUILD_ID} on ${env.JENKINS_URL}"
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
