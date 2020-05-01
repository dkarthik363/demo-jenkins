pipeline {

	agent any

	stages{
	stage('Build'){
		steps{
			bat 'gradle clean build'
		}
		post{
		success{
			echo 'Now archiving...'
			archiveArtifacts artifacts: '**/build/libs/*.war'
		}

		}

	}
	stage('Deploy to staging'){
	steps{
	  build job: 'deploy-to-staging'
	}
	}	

	}
 }
