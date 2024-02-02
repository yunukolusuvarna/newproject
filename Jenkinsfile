pipeline {
    agent any

    stages {
        stage('Clone-Repo') {
	    	steps {
	        	checkout scm
	    	}
        }

        stage('Compile') {
            steps {
                sh 'mvn clean compile'
            }
        }

        stage('Package as WAR') {
            steps {
                sh 'mvn package'
            }
        }
	stage('Deployment') {
            steps {
                sh 'sshpass -p staragile scp -o StrictHostKeyChecking=no target/gamutkart.war staragile@172.31.95.76:/root/apache-tomcat-9.0.85/webapps'
            }
        }

    }
}
