pipeline {
    agent any

    stages {
        stage('Build') {
        	steps {
                bat 'mvn clean install -DskipTests'
            }
        }
        stage('Deploy to CloudHub') {
        	steps {
        		bat 'set client_id=4563c4fe43a84132b283442580d88a7b'
        		bat 'set client_secret=F7074D23B5F14571BB5F483F90058b5c'
                bat 'mvn package deploy -DskipTests -DmuleDeploy -Dap.client_id=%client_id% -Dap.client_secret=%client_secret% -Dencrypt.key=secure12345'
            }
        }
   	}
}    