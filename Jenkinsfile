pipeline {
    agent any
    
    options {
    	timestamps()
    	ansiColor('xterm')  
  }
    
    environment {
    	AP_CLIENT_ID = credentials('ap.client_id')
    	AP_CLIENT_SECRET = credentials('ap.client_secret')
    	ENCRYPT_KEY = credentials('encrypt.key')
    }

    stages {
        stage('Build') {
        	steps {
                sh 'mvn clean install -Dencrypt.key=${ENCRYPT_KEY}'
            }
        }
        stage('Deploy to CloudHub') {
        	steps {
                sh 'mvn mule:deploy -DmuleDeploy -Dmule.artifact=./target/mico-customer-sapi-1.0.0-SNAPSHOT-mule-application.jar -Dap.client_id=${AP_CLIENT_ID} -Dap.client_secret=${AP_CLIENT_SECRET} -Dencrypt.key=${ENCRYPT_KEY}'
            }
        }
   	}
}    
