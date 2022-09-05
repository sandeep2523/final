pipeline{
	agent any
	
	stages{
		stage("DOCKER BUILD"){
			steps{
				echo "BUILD stage"
				sh ''' 
					ls
					cd /var/lib/jenkins/workspace/test
					docker build -t sandeep123 .
				'''
			}
		}
		stage("DOCKER TAG"){
	                 steps{
				sh 'docker image ls'
				sh 'docker tag sandeep123 sandeep2523/jenkins:4.10'
			}
		}
		stage("DOCKER PUSH"){
	                 steps{
			        sh 'docker image ls'
				sh 'docker push sandeep2523/jenkins:4.10'
				echo "Docker image pushed to docker hub successfuly"
			}
		}
		
		stage("Docker-run"){
			steps{
				echo "Running container"
				sh 'docker run -it -d -p 8040:8080 --name sandeep-tomcat4 sandeep2523/jenkins:4.10'
				sh 'docker ps'
				
			}
		}
	}
}
