pipeline {
  agent any
  environment {
	branchName = 'NotificationService'
  }
  stages {
      stage('for the main branch') {
          when {
              branch 'main'
          }
          steps {
			echo "${GIT_BRANCH} .. ${GIT_COMMIT} .. ${GIT_URL}" 
			echo "${env.BUILD_USER} .."
		    echo "##### scm varaibles branch name:....... $env.branchName.. $env.branch"
		    echo 'this only runs for main branch commits.... '
			//build job: 'CommonService-BuildAll', parameters: [[$class: 'StringParameterValue', name: 'buildBranch', value: '$env.branchName']]
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
