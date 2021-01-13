pipeline {
    agent any
    
    environment {
    	AP_CLIENT_ID = credentials('ap.client_id')
    	AP_CLIENT_SECRET = credentials('ap.client_secret')
    	ENCRYPT_KEY = credentials('encrypt.key')
    }

    stages {
        stage('Build') {
        	steps {
                bat "mvn clean install -Dencrypt.key=${ENCRYPT_KEY}"
            }
        }
        stage('Deploy to CloudHub') {
        	steps {
                bat 'mvn package deploy -DmuleDeploy -Dap.client_id=${AP_CLIENT_ID} -Dap.client_secret=${AP_CLIENT_SECRET} -Dencrypt.key=${ENCRYPT_KEY}'
            }
        }
   	}
}    
