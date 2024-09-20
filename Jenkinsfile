pipeline {
    agent any

    tools {
        maven 'Homebrew Maven' // Käytä nimeä, jonka annoit asennukselle
    }

    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/annikannisto/Tuntiteht.git', branch: 'main'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean install'
            }
        }

        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }

        stage('Code Coverage') {
            steps {
                jacoco execPattern: '**/target/jacoco.exec'
            }
        }
    }

    post {
        always {
            junit '**/target/surefire-reports/*.xml'
            jacoco execPattern: '**/target/jacoco.exec'
        }
    }
}
