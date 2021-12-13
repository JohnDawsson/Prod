pipeline {
environment {
    BRANCH_NAME = "${env.BRANCH_NAME}"
}
agent any
stages{
    stage('Build-Initiator-Info'){
            steps{
                sh 'echo "Send Info"'
            }
    }
    stage('Build') {
        steps{
             testcompletetest credentialsId: 'tester',
          executorType: 'TE',
          launchType: 'lcRoutine',
          project: 'TestProject1',
          routine: 'Test1',
          suite: 'ProjectSuite1\\ProjectSuite1.pjs',
          unit: 'Unit1',
          useTCService: true
       }
             catchError {
                sh 'echo "This is build"'
            }
         }
         post {
            success {
                echo 'Compile Stage Successful . . .'
            }
            failure {
                echo 'Compile stage failed'
                error('Stopping early…')

             }
    }
   }
  stage ('Deploy To Prod'){
  input{
    message "Do you want to proceed for production deployment?"
  }
    steps {
                sh 'echo "Deploy into Prod"'

              }
        }
  }
   }
