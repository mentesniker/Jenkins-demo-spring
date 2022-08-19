

pipeline {
    agent any
    environment { 
        CC = 'clang'
        // Using returnStdout
        AWS_ACCESS_KEY_ID     = credentials('jenkins-aws-secret-key-id')
        stDought = """${sh(
                returnStdout: true,
                script: 'echo "clang"'
            )}""" 
        // Using returnStatus
        EXIT_STATUS = """${sh(
                returnStatus: true,
                script: 'exit 1'
            )}"""
    }
    //parameters {
    //    string(name: 'Greeting', defaultValue: 'Hello', description: 'How should I greet the world?')
    //}
    stages {
        stage('Example') {
            when {
                expression {
                    env.BRANCH_NAME == 'main'
                }
            }
            steps {
                echo "Running ${env.BUILD_ID} on ${env.JENKINS_URL}"
                echo "${env.BRANCH_NAME}"
            }
        }
        stage('Example2') {
            environment { 
                DEBUG_FLAGS = '-g'
            }
            steps {
                sh 'printenv'
            }
        }
        stage('Build') {
            steps {
                sh 'mvn test'
                echo 'Building..'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Deploy') {
            steps {
                sh 'echo publish'
            }
        }
    }
    post {
        always {
            echo 'always'
        }
        failure {
            echo 'F'
        }
    }
}
