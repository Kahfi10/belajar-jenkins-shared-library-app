@Library('belajar-jenkins-shared-library@main') _

import kahfi.jenkins.Output;

pipeline {
    agent any
    
    stages {
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