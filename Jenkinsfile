pipeline {
	agent any
	stages {
		stage('Build') {
			steps {
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
	}
}
