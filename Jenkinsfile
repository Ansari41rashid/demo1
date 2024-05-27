pipeline {
    agent any
	tools {
	    maven 'maven-3.9.7'
	    git 'git-2.25.1'	
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
		    sh 'mvn clean install' '-D skiptest=true'
	   }
	}
    }
}
		
    
