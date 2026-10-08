pipeline {
    agent any

    stages {

        stage('Build') {
            steps {
                sh 'mvn clean'
            }
        }

        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }

        stage('Package') {
            steps {
                sh 'mvn package'
            }
        }

        stage('Archive') {
            steps {
                archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
            }
        }

        stage('Deploy') {
            steps {
                sh 'echo "Deploying application..."'
                sh 'cp target/*.jar /tmp/maven-practice.jar'
                sh 'echo "Application deployed successfully!"'
            }
        }

    }

    post {
        success {
            echo '🎉 Pipeline completed successfully!'
        }
    }
}
