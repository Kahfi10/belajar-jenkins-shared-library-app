@Library('belajar-jenkins-shared-library@main') _

import kahfi.jenkins.Output;

pipeline {
    agent any
    
    stages {
        stage('Build Maven Project') {
            steps {
                script {
                   maven(['clean', 'install'] )
                }
            }
        }

        stage('global variable') {
            steps {
                script {
                    echo author.name()
                    echo author.channel()
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
                    helloWorld()
                }
            }
        }
    }
}