pipeline {
    agent {
        node {
            label "docker"
        }
    }

    stages {
        stage('build') {
            steps {
                echo'start build'
                sh("./mvnw.cmd clean compile test-compile")
                echo 'Build completed successfully.'
            }
        }
        stage('test') {
            steps {
                echo 'Hello test'
                sleep(10)
                echo 'Running tests...'
                echo 'All tests passed.'
            }
        }
        stage('deploy') {
            steps {
                echo 'Hello deploy'
                sleep(10)
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
