pipeline {
    agent any

    stages {
        stage('GIT Clone') {
            steps {
                echo 'This stage is cloned code from GitHub'
                git branch: 'main', url: 'https://github.com/kumara-swamy-daraveni/mindcircuit16d.git'
            }
        }

        stage('Maven Build') {
            steps {
                echo 'This stage is to build code using Maven'
                sh 'mvn clean install'
            }
        }
        stage('Deploy to Tomcat') {
            steps {
                echo 'This stage is to deploy code using Tomcat'
				deploy adapters: [tomcat9(alternativeDeploymentContext: '', credentialsId: 'tomcat', path: '', url: 'http://ec2-54-210-32-27.compute-1.amazonaws.com:8080/')], contextPath: 'Sample-APP', war: '**/*.war'
            }
        }
    }
}
