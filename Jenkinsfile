pipeline {
  agent any
  environment {
	branchName = 'NotificationService'
	devServer = '192.168.0.125-qa-server'
	userid = 'administrator'
	password = 'LnTdesPTD@2600c'
  }
  stages {
		stage('Deployment to QA (192.168.0.125) server') {
		  when {
			expression {
				return env.BRANCH_NAME == 'main' || env.BRANCH_NAME == 'NotificationService'
			}
		  }

		  steps {
			echo 'deploying the $env.branchName in $env.devServer environment '
			build job: 'CommonService-BuildAll', parameters: [[$class: 'StringParameterValue', name: 'buildBranch', value: '$env.branchName']]
			build job: 'deploy_common_services', parameters: [[$class: 'StringParameterValue', name: 'userid', value: '$env.userid'],
															  [$class: 'StringParameterValue', name: 'password', value: '$env.password'],
															  [$class: 'StringParameterValue', name: 'DeploymentServer', value: '$env.devServer']]
		  }
		}
		
		stage('for the main branch') {
		  when {
			  branch 'feature*'
		  }

		  steps {
			echo "${GIT_BRANCH} .. ${GIT_COMMIT} .. ${GIT_URL}" 
			echo "##### scm varaibles branch name:....... $env.branchName.. env.BRANCH_NAME"
			echo 'this only runs for main branch commits.... '
			//build job: 'CommonService-BuildAll', parameters: [[$class: 'StringParameterValue', name: 'buildBranch', value: '$env.branchName']]
		  }
		}
		stage('build all for these barnches [main, NotificationService]') {
				when {
					 expression {
						return env.BRANCH_NAME != 'main' || env.BRANCH_NAME != 'NotificationService'
					}
				}
				steps {
					echo '### build for main || NotificationService branches'
				  //build job: 'CommonService-BuildAll', parameters: [[$class: 'StringParameterValue', name: 'buildBranch', value: 'NotificationService']]
				}
		}
		stage('for the feature branch starts with TPD') {
				when {
					branch 'TPD*'
				}
				steps {
					echo '### this only runs for main branch commits'
				  build job: 'CommonService-BuildAll', parameters: [[$class: 'StringParameterValue', name: 'buildBranch', value: 'NotificationService']]
				}
		  // echo "$BUILD_USER .... $BUILD_USER_ID" // No such property: BUILD_USER for class: groovy.lang.Binding
		  //echo "${env.BUILD_USER} .." //not working null
		  /* not working
		  wrap([$class: 'BuildUser']) {
			echo "$[BUILD_USER] ...."
		  }*/
		}
		
  }
}
