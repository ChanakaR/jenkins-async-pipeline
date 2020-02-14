pipeline{
    agent {
        docker { image 'orangehrm/orangehrm-environment-images:dev-7.2-centos-orange'}
    }
    stages {
        stage('Build') {
            steps {
                echo "Hello World 1"
                echo "Hello World 2"
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