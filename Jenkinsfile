pipeline {
	agent any
    	stages {
        	step('Build') {
            	sh "./gradlew build --no-daemon"
                archiveArtifacts artifacts: 'dist/trainSchedule.zip', fingerprint: true
            }
            step('Deploy') {
            	sh "sshpass -p jenkins -v ssh -tt -o StrictHostKeyChecking=no deploy@44.204.4.25 'systemctl stop train-schedule'"
                sh "sshpass -p jenkins -v scp -tt -o StrictHostKeyChecking=no dist/trainSchedule.zip deploy@44.204.4.25:/opt/train-schedule/trainSchedule.zip"
            	sh "sshpass -p jenkins -v ssh -tt -o StrictHostKeyChecking=no deploy@44.204.4.25 'unzip -o /opt/train-schedule/trainSchedule.zip'"
            	sh "sshpass -p jenkins -v ssh -tt -o StrictHostKeyChecking=no deploy@44.204.4.25 'systemctl start train-schedule'"
            }
        }
}
