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
			echo "$BUILD_USER .... $BUILD_USER_ID"
		    echo "##### scm varaibles branch name:....... $env.branchName.. $env.branch"
		    echo 'this only runs for main branch commits.... '
			//build job: 'CommonService-BuildAll', parameters: [[$class: 'StringParameterValue', name: 'buildBranch', value: '$env.branchName']]
          }
		  
		  //echo "${env.BUILD_USER} .." //not working null
		  /* not working
		  wrap([$class: 'BuildUser']) {
		  echo "$[BUILD_USER] ...."
		}*/
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
