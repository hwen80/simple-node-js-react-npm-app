pipeline {
	agent {
		docker {
			image 'node:6-alpine'
				args '-p 3000:3000'
		}
	}
	environment {
		CI = 'true'
	}
	stages {
		stage('Build') {
			steps {
				sh 'npm i'
			}
		}
		stage('Test') {
			steps {
				sh './jenkins/scripts/test.sh'
			}
		}
		stage('Deliver') {
			steps {
				sh './jenkins/scripts/deliver.sh'
				input message: 'Finished? (click proceed)'
				sh './jenkins/script/kill.sh'
			}
		}
	}
}
