pipeline{
	agent any
	stages{
		stage("Pull Latest Image"){
			steps{
				sh "docker pull ${LatestImage}"
			}
		}
		stage("Start Grid"){
			steps{
				sh "docker-compose up ${GridHubNodeCmd}"
			}
		}
		stage("Run Test"){
			steps{
				sh "docker-compose up ${SuiteFiles}"
			}
		}
	}
	post{
		always{
			archiveArtifacts artifacts: 'output/**'
			sh "docker-compose down"
			
			
		}
	}
}
