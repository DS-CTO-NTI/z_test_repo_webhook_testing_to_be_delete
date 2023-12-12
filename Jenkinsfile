pipeline {
  agent any
  environment {
	branchName = 'NotificationService'
	devServer = '192.168.0.125-qa-server'
	userid = 'administrator'
	password = 'LnTdesPTD@2600c'
  }
  stages {
		stage('build all for these barnches [main, NotificationService]') {
				when {
					 expression {
						return env.BRANCH_NAME == 'main' || env.BRANCH_NAME == 'NotificationService'
					}
				}
				steps {
					echo 'deploying the env.BRANCH_NAME $env.branchName, $env.userid, $env.password in $env.devServer environment updated on Dec 12 at 11am'
					echo '### build for main || NotificationService branches'
					//build job: 'CommonService-BuildAll', parameters: [[$class: 'StringParameterValue', name: 'buildBranch', value: '$env.branchName']]
					build job: 'deploy_common_services', parameters: [[$class: 'StringParameterValue', name: 'userid', value: 'administrator'],
																  [$class: 'StringParameterValue', name: 'password', value: 'LnTdesPTD@2600c'],
																  [$class: 'StringParameterValue', name: 'DeploymentServer', value: '192.168.0.125-qa-server']]
				}
		}
		stage('Getting user name and password') {
			steps {
			   withCredentials([[$class: 'UsernamePasswordMultiBinding', credentialsId: 'jenkins-docker-ssh', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD']]) {
				sh """
				echo uname=$USERNAME pwd=$PASSWORD
				"""
				}
			}
		}
  }
}
