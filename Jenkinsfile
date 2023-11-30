pipeline {
  agent any
  stages {
      stage('for the main branch') {
          when {
              branch 'main'
          }
          steps {
              echo 'this only runs for main branch commits'
			  build job: 'CommonService-BuildAll', parameters: [[$class: 'StringParameterValue', name: 'buildBranch', value: 'NotificationService']]
          }
      }
  }
}
