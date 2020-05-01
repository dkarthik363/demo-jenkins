pipeline{

	agent any

	stages{
	stage('Build'){
		steps{
			sh 'gradle clean build'
		}
		post{
		success{
			echo 'Now archiving...'
			archiveArtifacts artifacts: '**/build/libs/*.war'
		}

		}

	}	

	}
}
