pipeline {
	agent any
	environment {
		PATH+EXTRA = '/usr/local/bin'
	}
    stages {
        stage('Build') { 
            steps {
		withEnv(['PATH+EXTRA=/usr/local/bin']) {
			sh 'terraform --version'
		}
            }
        }
    }
}
