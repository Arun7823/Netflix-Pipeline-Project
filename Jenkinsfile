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
                // Build your project using Maven
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
                // Deploy your application to a server
                // Replace 'L4-Pipeline' with the appropriate in Jenkins job name or use ${env.WORKSPACE} for dynamic workspace path
                sh 'scp ${WORKSPACE}/target/NETFLIX-1.2.2.war root@13.126.240.217:/root/apache-tomcat-9.0.91/webapps/'
            }
        }
    }
    post {
        always {
            // Clean up or notify on completion
            echo 'Pipeline finished'
        }
        failure {
            // Actions to take in case of failure
            echo 'Pipeline failed'
        }
    }
}
