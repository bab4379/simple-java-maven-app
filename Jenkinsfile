pipeline {
	agent any
	environment {
		PATH= '/usr/local/bin'
	}
    stages {
        stage('Build') { 
            steps {
		sh 'terraform --version'
            }
        }
    }
}
