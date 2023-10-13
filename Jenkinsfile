pipeline {
    agent any
    
    tools {
        maven "maven 3.9.4"
    }

    stages {
        stage('Checkout code') {
            steps {
                timestamps {
                    git branch: 'development', credentialsId: 'git cred', url: 'https://github.com/Organi2/maven-web-application.git'
                }
            }
        }

        stage('Check Java Version') {
            steps {
                timestamps {
                    sh 'java --version'
                }
            }
        }

        stage('Build Package') {
            steps {
                timestamps {
                    bat "mvn clean package"
                }
            }
        }

        stage('Sonar Report') {
            steps {
                timestamps {
                    bat "mvn sonar:sonar"
                }
            }
        }

        stage('Upload Artifacts') {
            steps {
                timestamps {
                    bat "mvn deploy"
                }
            }
        }

        stage('Deploy to Tomcat') {
            steps {
                timestamps {
                    bat "copy C:\\ProgramData\\Jenkins\\.jenkins\\workspace\\declarative\\target\\maven-web-application.war C:\\Users\\ADMIN\\Downloads\\apache-tomcat-9.0.73\\apache-tomcat-9.0.73\\webapps"
                }
            }
        }
    }
}
