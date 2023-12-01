pipeline {
  agent any
  environement {
	branchName = 'NotificationService'
  }
  stages {
      stage('for the main branch') {
          when {
              branch 'main'
          }
          steps {
			echo "${GIT_BRANCH}"
			echo "${GIT_URL}"
			echo "${GIT_COMMIT}"
			  echo ##### scm varaibles branch name:....... $env.branchName
              echo 'this only runs for main branch commits.... '
			  build job: 'CommonService-BuildAll', parameters: [[$class: 'StringParameterValue', name: 'buildBranch', value: 'NotificationService']]
          }
      }
       stage('for the feature branch') {
                when {
                    branch 'TPD*'
                }
                steps {
                    echo '### this only runs for main branch commits'
      			  build job: 'CommonService-BuildAll', parameters: [[$class: 'StringParameterValue', name: 'buildBranch', value: 'NotificationService']]
                }
            }
  }
}
