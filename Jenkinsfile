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
}
