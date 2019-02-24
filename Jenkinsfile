pipeline {
	agent any         
		stages {                 
			stage('Prepare') {                         
				steps {  
					sh 'npm start'                            
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
