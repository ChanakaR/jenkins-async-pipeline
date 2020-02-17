pipeline{
    agent any
    environment {
        USER = 'Chanaka'
        HOST = 'Bee'
    }
    stages {
        stage('Run Tests') {
            parallel {
                stage('Test On Windows') {
                    steps {
                        echo "Test Windows Parallel 1"
                    }
                    post {
                        always {
                            echo "Test Windows Paralled echo"
                        }
                    }
                }
                stage('Test On Linux') {
                    steps {
                        echo "Test Linux Parallel 1"
                    }
                    post {
                        always {
                            echo "Test Linux Paralled echo"
                        }
                    }
                }
            }
        }
        stage('Build') {
            steps {
                echo "Hello World from ${USER}"
                echo "Hello World from ${HOST}"
            }
        }
    }
    post{
        always {
            echo "This runs always"
        }
        success {
            echo "This will run only if successful"
        }
        failure {
            echo "This will run only if failed"
        }
        unstable {
            echo "This will run only if the run was marked as unstable"
        }
        changed {
            echo 'This will run only if the state of the Pipeline has changed'
            echo 'For example, if the Pipeline was previously failing but is now successful'
        }
    }
}