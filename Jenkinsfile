pipeline{

	agent any

	environment {
		DOCKERHUB_CREDENTIALS=credentials('2160003120')
	}

	stages {

		stage('Build') {

			steps {
				sh 'docker build -t 2160003120/2048:latest .'
			}
		}

		stage('Login') {

			steps {
				sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
			}
		}

		stage('Push') {

			steps {
				sh 'docker push 2160003120/2048:latest'
			}
		}
	}

	post {
		always {
			sh 'docker logout'
		}
	}

}