pipeline {
    agent {
        node {
            label "docker"
        }
    }

    stages {
        stage('build') {
            steps {
                echo 'Hello build'
                echo 'Building the project...'
                echo 'Build complete.'
            }
        }
        stage('test') {
            steps {
                echo 'Hello test'
                echo 'Running tests...'
                echo 'All tests passed.'
            }
        }
        stage('deploy') {
            steps {
                echo 'Hello deploy'
                echo 'Deploying the application...'
                echo 'Deployment successful.'
            }
        }
    }

    post {
        always {
            echo 'This will always run after the stages.'
        }
        success {
            echo 'This will run only if the pipeline succeeds.'
        }
        failure {
            echo 'This will run only if the pipeline fails.'
        }
        cleanup {
            echo 'This will run at the end, regardless of the pipeline result.'
        }
    }
}
