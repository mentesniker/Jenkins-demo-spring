pipeline {
    agent {
        docker { image 'maven' }
    }
    stages {
        stage('Test') {
            steps {
                echo 'mvn test'
            }
        }
        stage('Deploy') {
            steps {
                sh 'echo publish'
            }
        }
    }
}
