pipeline {
    agent any

    tools {
        maven "maven"
    }

    stages {

        stage('Checkout') {
            steps {
                git branch: 'dev', url: 'https://github.com/saiprasad1715/maven-webapplication-project-kkfunda.git'
            }
        }
        stage('Build') {
            steps {
                sh "mvn clean package"
            }
        }
        stage('SQ report') {
            steps {
                sh "mvn sonar:sonar"
            }
        }
        stage('deploy to nexus') {
            steps {
                sh "mvn deploy"
            }
        }
         stage('Deploy to tomcat')
	 {
	   steps
	   {
	      sh '''
            curl -u sai:9391105070 --upload-file target/maven-web-application.war "http://13.127.79.44:8080/manager/text/deploy?path=/maven-web-application&update=true"
            '''
	   }
	 }
    }
}    
