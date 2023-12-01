pipeline {
  agent any
  stages {
      stage('for the main branch') {
          when {
              branch 'main'
          }
          steps {
			  echo scm varaibles branch name:....... scmVars.GIT_BRANCH
              echo 'this only runs for main branch commits.... '
			  build job: 'CommonService-BuildAll', parameters: [[$class: 'StringParameterValue', name: 'buildBranch', value: 'NotificationService']]
          }
      }
       stage('for the feature branch') {
                when {
                    branch 'TPD*'
                }
                steps {
                    echo 'this only runs for main branch commits'
      			  build job: 'CommonService-BuildAll', parameters: [[$class: 'StringParameterValue', name: 'buildBranch', value: 'NotificationService']]
                }
            }
  }
}
