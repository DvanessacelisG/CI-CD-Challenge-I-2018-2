pipeline {
	agent any     
	    	environment {
            		DockerUser = credentials('DockerUser')
            		DockerPass = credentials('DockerPass')
			version = "${env.BUILD_ID}"
       			 }
		stages {                 
			stage('Prepare') {                         
				steps {  
					                            
					echo 'Preparing..'
				}                 
			}                 
			stage('Build') {                         
				steps {                                 
					
					sh 'docker build . --tag=challengeimage'
					echo 'Building..'                         
				}                 
			}                 
			stage('Test') {                         
				steps {
					sh 'docker run challengeimage npm test'
					echo 'Testing...'                        
				}                 
			}
			stage('push') {
				steps {	
					sh 'docker login -u $DockerUser -p $DockerPass'
                    			sh 'docker tag challengeimage:latest vanessacelis/challengedh:latest'
                    			sh 'docker push vanessacelis/challengedh:latest'
					echo 'pushing'
				}
			}                 
			stage('Deploy') {                         
				steps { 
					
					
					input message: 'Deploy? (Click "Proceed" to continue)'
					sh 'docker stop $(docker ps -a -q)'
					sh 'docker run -d -p 8000:8000 challengeimage'
					sh 'docker container prune --force'
					sh 'docker rmi $(docker images -f dangling=true -q)'
					echo 'Deploying....'                                     					
				}                 
			}         
		} 
} 
