pipeline {
	agent any
    	stages {
        	stage('Build') {
		steps{
			sh "./gradlew build --no-daemon"
			archiveArtifacts artifacts: 'dist/trainSchedule.zip', fingerprint: true
		}
            }
            stage('Deploy') {
	    	steps{
            	sh "sshpass -p jenkins -v ssh -tt -o StrictHostKeyChecking=no deploy@44.204.4.25 'sudo systemctl stop train-schedule'"
                sh "sshpass -p jenkins -v scp -o StrictHostKeyChecking=no dist/trainSchedule.zip deploy@44.204.4.25:/opt/train-schedule/trainSchedule.zip"
            	sh "sshpass -p jenkins -v ssh -tt -o StrictHostKeyChecking=no deploy@44.204.4.25 'sudo unzip -o /opt/train-schedule/trainSchedule.zip -d /opt/train-schedule/'"
            	sh "sshpass -p jenkins -v ssh -tt -o StrictHostKeyChecking=no deploy@44.204.4.25 'sudo systemctl start train-schedule'"
		}
            }
        }
}
