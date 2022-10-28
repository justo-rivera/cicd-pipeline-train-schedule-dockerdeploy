pipeline {
	agent any
	stages {
		stage('Build') {
			steps{
				sh './gradlew build'
				sh './gradlew npm_start'
			}
		}
    	}
	post {
		always {
			archiveArtifacts artifacts: 'dist/trainSchedule.zip', fingerprint: true
		}
	}
}
