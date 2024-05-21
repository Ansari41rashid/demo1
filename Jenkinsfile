pipeline {
    agent any
	tools{
	    maven 'maven-3.6.3'
    }
	 stages {
        stage('Checkout the code') {
            steps{
                git url:'https://github.com/Ansari41rashid/demo1.git', branch: 'master'
			}
		}
		stage('build the code'){
		    steps{
			    sh 'mvn clean package'
			}
		}
	 }
}
		
    
