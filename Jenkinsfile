pipeline {
    agent none

    environment {
       AUTHOR = "KAHFI"
      }
    
    // triggers {
    //     cron('H/5  k* * * *')
    // }
    
    parameters {
        string(name: 'name', defaultValue: 'main', description: 'Branch to build')
        text(name: 'description', defaultValue: 'This is a sample Jenkins pipeline', description: 'Description of the build')
        booleanParam(name: 'runTests', defaultValue: true, description: 'Whether to run tests or not')
        choice(name: 'environment', choices: ['development', 'staging', 'production'], description: 'Select the deployment environment')
        password(name: 'APP_PSW', defaultValue: 'defaultPassword', description: 'Password for the application')
    }
    
    options {
        disableConcurrentBuilds()
        timeout(time: 10, unit: 'MINUTES')
    }
    stages {
        stages('preparation') {
            parallel {
                stage('prepare java') {
                    agent {
                        node {
                            label "docker"
                        }                    
                    }
                    steps {
                        echo 'prepare java'
                        sleep(5)
                    }
                }
                stage('prepare maven') {
                    agent {
                        node {
                            label "docker"
                        }                    
                    }
                    steps {
                        echo 'prepare maven'
                        sleep(5)
                    }
                }
            }
        }
        stage('parameter') {
            agent {
                node {
                    label "docker"
                }
            }
            steps {
                echo "Branch to build: ${params.name}"
                echo "Build description: ${params.description}"
                echo "Run tests: ${params.runTests}"
                echo "Deployment environment: ${params.environment}"
            }
        }

        stage('prepare') {

            environment {
                APP = credentials('kahfi_rahasia')
            }

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
                echo "app username : ${APP_USR}"
                sh "echo 'App password : ${APP_PSW}' > secret.txt"
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
            input {
                message "can we deploy"
                ok "Yes, let's deploy!"
                submitter "admin"
                parameters {
                    choice(name: 'DEPLOY_ENV', choices: ['development', 'staging', 'production'], description: 'Select the deployment environment')
                }
            }
            agent {
                node {
                    label "docker"
                }
            }
            steps {
                echo "Deploying to environment: ${params.DEPLOY_ENV}"
                echo 'Hello deploy'
            }
        }
            stage('release') {
        when {
            expression {
                return params.runTests
            }
        }
        agent {
            node {
                label "docker"
            }
        }
        steps {
            echo 'Hello release'
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
