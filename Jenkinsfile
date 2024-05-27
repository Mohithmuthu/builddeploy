pipeline {
    agent any

    tools {
        maven 'Maven_3.6.3'  // Ensure this matches the Maven installation name in Jenkins
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'master', url: 'https://github.com/Mohithmuthu/builddeploy.git', credentialsId: 'mohith1234'
            }
        }

        stage('Compile Stage') {
            steps {
                sh 'mvn compile'
            }
        }

        stage('Test Stage') {
            steps {
                sh 'mvn test'
            }
        }

        stage('Package Stage') {
            steps {
                sh 'mvn package'
            }
        }
    }
}
