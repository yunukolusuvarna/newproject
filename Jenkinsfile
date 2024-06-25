pipeline {
    agent any
     tools {
        maven 'maven'  // Use the name configured in Global Tool Configuration
    } 
    stages {
        stage('Clone-Repo') {
	    	steps {
	        	git url: 'https://github.com/yunukolusuvarna/newproject.git',
				branch:'main'
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
		sh ' -sshpass -p vpath scp target/gamutkart.war vpath@172.31.34.57/:/home/vpath/apache-tomcat-8.5.100/webapps'
	}
    }
}
}
