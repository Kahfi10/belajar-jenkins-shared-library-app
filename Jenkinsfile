@Library('belajar-jenkins-shared-library@main') _

pipeline {
    agent any
    
    stages {
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