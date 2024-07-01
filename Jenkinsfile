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
		sh '/usr/bin/sshpass -p root scp -o StrictHostKeyChecking=no target/gamutkart.war root@172.31.34.57:/home/root/apache-tomcat-8.5.100/webapps'
	}
    }
}
}
