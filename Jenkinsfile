pipeline {
    agent any

    tools {
        jdk 'JDK21'       // Configure JDK 21 in Jenkins Global Tool Configuration
        maven 'Maven3'    // Configure Maven in Jenkins
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'master',
                    url: 'https://github.com/harshu3102/devops-demo.git',
                    credentialsId: 'your-credential-id'
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

        stage('Run') {
            steps {
                echo 'Running HelloWorld...'
                sh 'java -cp target/classes com.devops.demo.HelloWorld'
            }
        }
    }

    post {
        success {
            echo '✅ Build and run successful!'
        }
        failure {
            echo '❌ Build failed. Check logs.'
        }
    }
}
