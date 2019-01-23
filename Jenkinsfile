pipeline {
	agent any
	environment {
		PATH+EXTRA = '/usr/local/bin'
	}
    stages {
        stage('Build') { 
            steps {
		sh 'terraform --version'
            }
        }
    }
}
