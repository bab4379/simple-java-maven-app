pipeline {
	agent any
	environment {
		PATHEXTRA = '/usr/local/bin'
	}

    stages {
        stage('Build') { 
            steps {
                sh 'mvn -B -DskipTests clean package' 
                sh '/usr/local/bin/terraform -version' 

		//withEnv(['PATH+EXTRA=/usr/local/bin']) {
			//sh 'terraform --version'
		//}
            }
        }
	stage('Test') {
            steps {
                sh 'mvn test'
            }
            post {
                always {
                    junit 'target/surefire-reports/*.xml'
                }
            }
        }
	stage('Deliver') {
            steps {
                sh './jenkins/scripts/deliver.sh'
            }
        }
    }
}
