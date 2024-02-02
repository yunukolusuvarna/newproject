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
                sh 'cp target/gamutkart.war /home/staragile/Distros/apache-tomcat-9.0.85/webapps'
            }
        }

    }
}
