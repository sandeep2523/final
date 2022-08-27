pipeline{
	agent any
	
	stages{
		stage("git clone"){
			steps {
                git branch: 'test', url: 'https://github.com/sandeep2523/final.git'
            }
		}
		stage ('DOCKER Login') {
           steps {
               sh 'docker login -u="sandeep2523" -p="Sandeep@2523"'
            }
        }
		stage("DOCKER BUILD"){
			steps{
				echo "BUILD stage"
				sh ''' 
					cd /var/lib/jenkins/workspace/test
					docker build -t sandeep2523 .
				'''
			}
		}
		stage("DOCKER TAG"){
	                 steps{
				sh 'docker image ls'
				sh 'docker tag sandeep2523 sandeep2523/jenkins:3.10'
			}
		}
		stage("DOCKER PUSH"){
	                 steps{
			        sh 'docker image ls'
				sh 'docker push sandeep2523/jenkins:3.10'
				echo "Docker image pushed to docker hub successfuly"
			}
		}
		
		stage("Docker-run"){
			steps{
				echo "Running container"
				sh 'docker run -it -d -p 8050:8080 --name sandeep-tomcat3 sandeep2523/jenkins:3.10'
				sh 'docker ps'
				
			}
		}
	}
}
