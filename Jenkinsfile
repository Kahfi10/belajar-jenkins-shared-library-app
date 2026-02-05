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
            }
        }
            steps('test') {
                echo 'Hello test'
            }
        }
            steps('deploy') {
                echo 'Hello deploy'
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
