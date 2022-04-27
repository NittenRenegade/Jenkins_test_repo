pipeline {
	agent any
	environment {
		DISABLE_AUTH = 'true'
		DB_ENGINE = 'sqlite'
	}
	stages {
		stage('Build') {
			steps {
				echo "Database engine: ${DB_ENGINE}"
				timeout(time: 3, unit: 'SECONDS') {
					retry(5) {
						sh 'echo "Hello world!"'
					}
					sh '''
						echo "Multiline too"
						ls -lah
					'''
					}
				}
		}
		stage('Test') {
			steps {
				echo 'Some test here'
			}
		}
		stage('Sanity check') {
			steps {
				input "Does the staging environment look ok?"
			}
		}
	}
	post {
		always {
			echo "This will always run \n Auth=${DISABLE_AUTH}"}
		success {
			echo 'This will run always if successfull'}
		failure {
			echo 'This will run only if failured'}
		unstable {
			echo 'This will run only if bluid marked as unstable'}
		changed {
			echo 'This will run if build result changed'
			echo 'For example previous run Pipeline failure and now success'
			}
	}
}
