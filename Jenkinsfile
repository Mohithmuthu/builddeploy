pipeline {
    agent any

    tools {
        maven 'Maven_3.6.3'  // Ensure this matches the Maven installation name in Jenkins
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'feature14368-jenkis-first-stage', url: 'https://github.com/Mohithmuthu/builddeploy.git', credentialsId: 'mohith1234'
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

    post {
        success {
            echo 'Build succeeded!'
            archiveArtifacts artifacts: '*/target/.jar', allowEmptyArchive: true
        }
        failure {
            echo 'Build failed!'
            mail to: 'your-email@example.com',
                 subject: "Failed Pipeline: ${currentBuild.fullDisplayName}",
                 body: "Something is wrong with ${env.JOB_NAME}:\n\n${env.BUILD_URL}"
        }
        always {
            junit 'target/surefire-reports/*.xml'
        }
    }
}
