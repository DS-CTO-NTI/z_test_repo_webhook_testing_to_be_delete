pipeline {
  agent any
  stages {
      stage('Hello') {
          steps {
              echo 'hello from Jenkinsfile ##########111 ##############............'
          }
      }
      stage('build') {
          steps {
               echo 'hello from Jenkinsfile ##########222 ##############............'
          }
      }
      stage('for the test branches') {
          when {
              branch 'test*'
          }
          steps {
              echo 'this only runs for webhook* branches3333 ##############............'
          }
      }
  }
}
