@Library('belajar-jenkins-shared-library@main') _

import kahfi.jenkins.Output;

pipeline {
    agent any
    
    stages {
        stage {
            steps {
                script {
                    maven('clean compile')
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