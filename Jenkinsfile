pipeline {
	agent any
	stages {
		stage('Build') {
			steps{
				sh './gradlew build --no-daemon'
			}
		}
    	}
	post {
		always {
			archiveArtifacts artifacts: 'dist/trainSchedule.zip', fingerprint: true
		}
	}
}
