pipeline {
  agent any
  stages {
      stage('Hello') {
          steps {
              echo 'hello from Jenkinsfile ##########123 ##############............######'
          }
      }
      stage('build') {
          steps {
               echo 'hello from Jenkinsfile ##########456 ##############............######'
          }
      }
      stage('for the webhook branch') {
          when {
              branch 'webhook*'
          }
          steps {
              echo 'this only runs for webhook* branches..### ###............***** 123 #########.'
          }
      }
  }
}
