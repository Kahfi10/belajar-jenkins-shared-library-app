pipeline {
    agent {
        node {
            label "docker"
        }
    }

    stages {
        stage('Hello') {
            steps {
                echo 'Hello World'
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
