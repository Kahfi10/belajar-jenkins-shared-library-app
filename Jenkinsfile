@Library('belajar-jenkins-shared-library@main') _

pipeline {
    agent any
    
    stages {
        stage('library resource') {
            steps {
                script {
                    def config = libraryResource 'config/build.json'
                    echo(config)
                }
            }

        }

        stage('hello person') {
            steps{
                script{
                    // Shared library vars/person.groovy defines method person(Map)
                    person.person([
                        firstName: 'ashabul',
                        lastName: 'kahfi'
                    ])
                }
            }
        }
        stage('Build Maven Project') {
            steps {
                script {
                    if (isUnix()) {
                        sh './mvnw clean compile test'
                    } else {
                        bat 'mvnw.cmd clean compile test'
                    }
                }
            }
        }

        stage('global variable') {
            steps {
                script {
                    echo(author())
                    echo(author.name())
                    echo(author.channel())
                }
            }
        }

        // Removed direct class call from shared library to avoid
        // Jenkins Sandbox/CPS method approval issues.
        stage('Hello World') {
            steps {
                script {
                    // Use shared library global step: vars/hello.groovy -> world()
                    hello.world()
                }
            }
        }
    }
}