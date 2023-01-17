pipeline {
	agent any
	stages {
		stage("Pull Latest Image"){
			steps{
				sh "docker pull ransomeli/selenium-docker2"
			}
		}
		stage("Start Grid") {
			steps{
				sh "docker-compose up -d hub chrome firefox"
			}
		}
		stage("Run Test"){
			steps{
				sh "docker-compose up search-module-aaca book-flight-module"
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