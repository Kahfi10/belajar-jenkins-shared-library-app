pipeline {
    agent none

    environment {
       AUTHOR = "KAHFI"
      }
    stages {
        stage('prepare') {
            agent {
                node {
                    label "docker"
                }
            }
            steps {
                echo "author: ${env.AUTHOR}"
                echo "start job : ${env.JOB_NAME}"
                echo "build number : ${env.BUILD_NUMBER}"
                echo "build url : ${env.BUILD_URL}"
            }
        }
        stage('build') {
            agent {
                node {
                    label "docker"
                }
            }
            steps {
                script {
                    for (int i = 0; i < 1; i++) {
                        echo "Hello build iteration ${i}"
                    }
                }
            }
        }
        stage('test') {
            agent {
                node {
                    label "docker"
                }
            }
            steps {
                script {
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
