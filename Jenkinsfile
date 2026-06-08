pipeline {
    agent any

    tools {
        maven 'Maven-3'
        jdk 'JDK-17'
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build JAR') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Archive JAR') {
            steps {
                archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
            }
        }

       // stage('Build Docker Image') {
            steps {
                sh 'docker build -t java-jar-pipeline:v1 .'
            }
        }
    }
}
