pipeline {
    agent any
    
    tools {
        maven "maven 3.9.4"
        jdk "jdk-11" // You can specify the desired JDK version here
    }

    stages {
        stage('Checkout code') {
            steps {
                git branch: 'development', credentialsId: 'git cred', url: 'https://github.com/Organi2/maven-web-application.git'
            }
        }

        stage('Check Java Version') {
            steps {
                sh 'java -version'
            }
        }

        stage('Build Package') {
            steps {
                bat "mvn clean package"
            }
        }

        stage('Sonar Report') {
            steps {
                bat "mvn sonar:sonar"
            }
        }

        stage('Upload Artifacts') {
            steps {
                bat "mvn deploy"
            }
        }

        stage('Deploy to Tomcat') {
            steps {
                bat "copy C:\\ProgramData\\Jenkins\\.jenkins\\workspace\\declarative\\target\\maven-web-application.war C:\\Users\\ADMIN\\Downloads\\apache-tomcat-9.0.73\\apache-tomcat-9.0.73\\webapps"
            }
        }
    }
}
