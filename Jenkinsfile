pipeline {
    agent any
    stages {
        stage('Compile') {
            steps {
                sh 'mvn clean package -DskipTests=true'
            }
        }
        stage('Unit Tests') {
            steps {
                sh 'mvn surefire:test'
            }
        }
         stage('Integration Tests') {
            steps {
                sh 'mvn failsafe:integration-test'
            }
        }
    }
    post {
        always {
            junit allowEmptyResults: true, testResults: "${WORKSPACE}/test-results/*.xml"

        }
        failure {
            sh 'echo "This is falure"'
        }
    }
}
