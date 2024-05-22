pipeline {
    agent any
	tools {
	    maven 'maven'
    }
	 stages {
        stage('Checkout the code') {
            steps {
                git url:'https://github.com/Ansari41rashid/demo1.git', branch: 'master'
			}
		}
         stage('compile') {
	     steps {
		     sh 'mvn compile'
			
		} 
	 }
         stage('build the code'){
	     steps{
		    sh 'mvn clean install'
	   }
	}
    }
}
		
    
