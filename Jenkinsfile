pipeline {
    agent any
     environment {
        PATH = "/opt/apache-maven-3.9.8/bin:$PATH"
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
			sh 'maven install'
		}
	}	
 
	stage ('Compile'){
	        steps {
			sh 'maven clean compile'
                }
	}

	stage('Run Tests') {
	    steps {
	       sh 'maven test'
	    }
	}
        stage('Package as WAR') {
            steps {
                sh 'maven package'
            }
        }
       
	stage('Deployment') {
	   steps {
		sh 'sshpass -p vpath scp target/gamutkart.war vpath@3.26.166.190/:/home/vpath/apache-tomcat-8.5.100/webapps'
	}
    }
}
}
