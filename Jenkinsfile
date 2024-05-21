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
		
		stages {
        stage('build docker image from dockerfile') {
            steps{
                sh 'docker image build -t vayhu.azurecr.io/demo1:${BUILD_NUMBER} .'
            }
        }
        
        stage('azure login and push the docker Image to ACR') {
            steps{
                withCredentials([usernamePassword(credentialsId: 'AZURE_ACR_Credentials', usernameVariable: 'username', passwordVariable: 'password')]) {
                        def dockerLogin = "docker login ${DOCKER_REGISTRY} -u ${ACR_USER} -p ${ACR_PASSWORD}"
                        sh dockerLogin 
                    }
                    
                    // Tag Docker image for ACR
                    def dockerTag = "docker tag ${DOCKER_IMAGE_NAME} ${DOCKER_REGISTRY}/${DOCKER_IMAGE_NAME}"
                    sh dockerTag
                    
                    // Push Docker image to ACR
                    def dockerPush = "docker push ${DOCKER_REGISTRY}/${DOCKER_IMAGE_NAME}"
                    sh dockerPush
                }
            }
        }
    }
}
