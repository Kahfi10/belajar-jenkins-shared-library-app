@Library('belajar-jenkins-shared-library@main') _

import kahfi.jenkins.Output;

pipeline {
    agent {
        docker {
            image 'maven:3.8.1-jdk-11'
            args '-v /root/.m2:/root/.m2'
        }
    }
    
    stages {
        stage('Build Maven Project') {
            steps {
                script {
                    maven(["clean", "compile", "test"])
                }
            }
        }

        stage('global variable') {
            steps {
                script {
                    echo (author())
                    echo (author.name())
                    echo (author.channel())
                }
            }
        }

        stage('hello kahfi') {
            steps {
                script {
                    Output.hello(this, 'Kahfi')
                }
            }
        }
        stage('Hello World') {
            steps {
                script {
                    hello.world()
                }
            }
        }
    }
}