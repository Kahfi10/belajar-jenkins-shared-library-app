pipeline {
    agent {
        node {
            label "docker"
        }
    }

    stages {
        stage('build') {
            steps {
                script {
                    for (int i = 0; i < 1; i++) {
                        echo "Hello build iteration ${i}"
                    }
                }
            }
        }
        stage('test') {
            steps {
                script{
                    def data = [
                        "firstName": "John",
                        "lastName": "Doe",
                    ]
                    writeJSON(file: 'data.json', json: data)
                }
                echo 'Hello test'
                sh("./mvnw test")
                echo 'Tests completed.'
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
