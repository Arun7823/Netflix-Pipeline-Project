pipeline {
    agent any
    tools {
        maven 'Maven'
        git   'Git'
        jdk   'JDK11'
    }
    stages {
        stage('Checkout') {
            steps {
                // Checkout the code from GitHub
                git branch: 'master', url: 'https://github.com/Arun7823/Netflix-Pipeline-Project.git'
            }
        }
        stage('Build') {
            steps {
                // Build your project, e.g., using Maven, Gradle, etc.
                sh 'mvn clean package'
            }
        }
        stage('Test') {
            steps {
                // Run tests
                sh 'mvn test'
            }
        }
        stage('Deploy') {
            steps {
                // Deploy your application, e.g., to a server
                sh 'sudo scp /var/lib/jenkins/workspace/L4-Pipeline/target/*.war /root/apache-tomcat-9.0.91/webapps'
            }
        }
    }
    post {
        always {
            // Clean up or notify on completion
            echo 'Pipeline finished'
        }
    }
}
