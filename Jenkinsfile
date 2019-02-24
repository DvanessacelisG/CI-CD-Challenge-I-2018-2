pipeline {
	agent any     
	    	environment {
            		DockerUser = credentials('DHubUser')
            		DockerPass = credentials('DHubPass')
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
					sh 'docker login -u $DHubUser -p $DHubPass'
                    			sh 'docker tag challengeimage:latest vanessacelis/challengedh:latest'
                    			sh 'docker push vanessacelis/challengeimage:latest'
					echo 'pushing'
				}
			}                 
			stage('Deploy') {                         
				steps {                                 
					echo 'Deploying....'                                     					
				}                 
			}         
		} 
} 
