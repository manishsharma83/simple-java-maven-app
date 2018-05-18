pipeline {
	agent any
	stages {
		stage('Build') {
			steps {
				sh 'mvn -B -DskipTests clean package'
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
		stage('APITest') {
			steps {
				echo 'API testing begins!!!'
			}
		}
	}
}
