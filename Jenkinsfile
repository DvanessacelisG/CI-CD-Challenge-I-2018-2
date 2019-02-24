pipeline {
	agent any         
		stages {                 
			stage('Prepare') {                         
				steps {  
					git url: https://github.com/DvanessacelisG/CI-CD-Challenge-I-2018-2.git                               
					echo 'Preparing..'
				}                 
			}                 
			stage('Build') {                         
				steps {                                 
					echo 'Building..'                         
				}                 
			}                 
			stage('Test') {                         
				steps {                                 
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
