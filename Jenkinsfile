pipeline {
	agent {
		docker {
			image 'maven:3-alpine' 
			args '-v /root/.m2:/root/.m2' 
		}
	}
	environment {
		PATH="/usr/local/bin:$PATH"
	}
    stages {
        stage('Build') { 
            steps {
                sh 'mvn -B -DskipTests clean package' 
		sh 'printenv | grep PATH'
		sh 'which terraform'
		sh 'terraform --version'
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
