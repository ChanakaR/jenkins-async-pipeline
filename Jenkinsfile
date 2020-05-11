pipeline{
    agent none
    environment {
        USER = 'Chanaka'
        HOST = 'Bee'
    }
    stages {
        stage('Run Tests') {
            parallel {
                stage('Test On Pyro') {
                    agent {
                        label "slave-pyro"
                    }
                    steps {
                        echo "Test On Slave"
                        echo "hello to pyro" >> /results/pyro.txt
                    }
                    post {
                        always {
                            echo "POST: Test on slave"
                        }
                    }
                }
                stage('Test On Linux') {
                    agent {
                        label "master"
                    }
                    steps {
                        echo "Test on Master"
                        echo "hello to master" >> /results/master.txt
                    }
                    post {
                        always {
                            echo "POST: Test on master"
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