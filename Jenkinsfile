pipeline{
	agent any
	stages{
		stage("Pull Latest Image"){
			steps{
				sh "docker pull jppamintuan/codeceptjs-api-dockerized-test:latest"
			}
		}
		stage("Run Test"){
			steps{
				sh "docker-compose -f docker-compose.yaml up --exit-code-from codeceptjs-api-dockerized-test --no-color"
			}
		}
	}
	post{
		always{
			archiveArtifacts artifacts: 'report_container/**'
			sh "docker-compose down"
		}
	}
}