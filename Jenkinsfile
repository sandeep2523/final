pipeline{
	agent any
	
	stages{
		stage("DOCKER BUILD"){
			steps{
				echo "BUILD stage"
				sh ''' 
					ls
					cd /var/lib/jenkins/workspace/final
					docker build -t sandeep2523/jenkins:1.10 .
				'''
			}
		}
		stage("DOCKER PUSH"){
	                 steps{
				sh 'docker image ls'
				sh 'docker push sandeep2523/jenkins:1.10'
				echo "Docker image pushed to docker hub successfuly"
			}
		}
		
		stage("Docker-run"){
			steps{
				echo "Running container"
				sh 'docker run -it -d -p 8060:8080 --name sandeep-tomcat sandeep2523/jenkins:1.10'
				sh 'docker ps'
				
			}
		}
	}
}
