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
			echo "##### scm varaibles branch name:....... $env.branchName.. "
			echo 'this only runs for main branch commits.... '
			//build job: 'CommonService-BuildAll', parameters: [[$class: 'StringParameterValue', name: 'buildBranch', value: '$env.branchName']]
		  }
		}
		stage('build all for these barnches [main, NotificationService]') {
				when {
					branch 'main || NotificationService'
				}
				steps {
					echo '### build for main || NotificationService branches'
				  //build job: 'CommonService-BuildAll', parameters: [[$class: 'StringParameterValue', name: 'buildBranch', value: 'NotificationService']]
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
		 // echo "$BUILD_USER .... $BUILD_USER_ID" // No such property: BUILD_USER for class: groovy.lang.Binding
		  //echo "${env.BUILD_USER} .." //not working null
		  /* not working
		  wrap([$class: 'BuildUser']) {
			echo "$[BUILD_USER] ...."
		  }*/
  }
}
