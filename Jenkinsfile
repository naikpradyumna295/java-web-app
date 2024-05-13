pipeline {
    agent any

    tools {
        maven 'maven3.9.6'
        jdk 'OpenJDK8'
    }

    stages {
        stage('checkout code') {
            steps {
                git branch: 'main', url: 'https://github.com/naikpradyumna295/java-web-app.git'
            }
        }
        stage('build code') {
            steps {
                sh 'mvn clean package'
            }
        }
        stage('Deployment') {
            steps {
                deploy adapters: [tomcat9(url: 'http://18.141.179.180:8080/', credentialsid: 'TomcatCreds')], war: 'target/*.war'
            }
        }
    }
}
