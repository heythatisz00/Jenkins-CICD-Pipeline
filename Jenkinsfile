pipeline {
    
    agent any
    
    environment {
        gitURL = 'https://github.com/heythatisz00/development.git'
        branch = 'master'
    }
    
    stages {
        stage('GitHub Code Checkout') {
            steps {
				echo "*****Checkout code*****"	
				//Delete everything in workspace to start fresh
				deleteDir()
				//Checkout the code
				git branch: "${branch}", url: "${gitURL}"
			}
        }
        
        stage('Program Build') {
            steps {
                sh 'javac hello.java'
                }
        }
        
		stage('Program Run') {
		    steps {
		         sh 'java hello'
		    }
		}
		
		stage('Notification') {
            steps {
                echo "mail for successful build"
                emailext body: 'Build Successful', recipientProviders: [developers()], subject: 'TestMail', to: 'xyz@gmail.com'
            }
        }
    }
}
