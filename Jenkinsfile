pipeline {
	agent any
	
	triggers {
        githubPush()
    }
	
	stages {
        stage('Code Checkout') {
            steps {
                checkout([
                    $class: 'GitSCM', 
                    branches: [[name: '*/master']], 
                    userRemoteConfigs: [[url: 'https://github.com/sandeepraina-dsd19/spring-boot-h2-war-tomcat.git']]
                ])
            }
        }

        stage('Code Build') {
            steps {
                 bat 'mvn clean package'
            }
        }

        stage('Start Tomcat') {
            steps {
                 bat 'start_tomcat.sh C:/apache-tomcat-9.0.62'
            }
        }
		
		stage('Deploy war file') {
            steps {
                 bat 'mvn tomcat7:deploy'
            }
        }

    }   
}