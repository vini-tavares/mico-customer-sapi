pipeline {
    agent any
    
    environment {
    	AP.CLIENT_ID = credentials('ap.client_id')
    	AP.CLIENT_SECRET = credentials('ap.client_secret')
    	ENCRYPT.KEY = credentials('encrypt.key')
    }

    stages {
        stage('Build') {
        	steps {
                bat "mvn clean install -Dencrypt.key=${ENCRYPT.KEY}"
            }
        }
        stage('Deploy to CloudHub') {
        	steps {
                bat 'mvn package deploy -DmuleDeploy -Dap.client_id=${AP.CLIENT_ID} -Dap.client_secret=${AP.CLIENT_SECRET} -Dencrypt.key=${ENCRYPT.KEY}'
            }
        }
   	}
}    
