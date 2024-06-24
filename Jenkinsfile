pipeline {
    agent any

    stages {
        stage('Clone-Repo') {
	    	steps {
	                checkout scm 'https://github.com/yunukolusuvarna/newproject.git'
	    	}
        }
	stage('Build') {
		steps {
			sh 'mvn install'
		}
	}	
 
	stage ('Compile'){
	        steps {
			sh 'mvn clean compile'
                }
	}

	stage('Run Tests') {
	    steps {
	       sh 'mvn test'
	    }
	}

        stage('Package as WAR') {
            steps {
                sh 'mvn package'
            }
        }
	stage('Deployment') {
	   steps {
		sh 'sshpass -p vpath scp target/gamutkart.war vpath@172.31.16.232:/home/vpath/apache-tomcat-8.5.100/webapps'
	}
    }
}
}
