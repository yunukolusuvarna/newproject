pipeline {
    agent any

    stages {
        stage('Clone-Repo') {
	    	steps {
	        	checkout scm
	    	}
        }
	 stage ('Build'){
	        steps {
			sh 'mvn clean install'
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
		sh 'sshpass -p staragile scp target/gamutkart.war staragile@172.31.84.250:/home/staragile/apache-tomcat-9.0.85/webapps/'
	}
    }
}
