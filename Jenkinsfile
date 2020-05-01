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
  	stage('Deploy to Production'){
	steps{
		timeout(time:5,unit:'DAYS'){
			input message: 'Approve prod deployment'
		}

		build job: 'deploy-to-prod'

	}
	post{
		success {
			echo 'code deployed to prod'
		}
		failure {
			echo 'Deployment failed' 
		}
	}

	}
	}
 }
