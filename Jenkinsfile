def gv

pipeline {
    agent any
    tools {
        maven 'maven'
    }
    stages {
        stage("init") {
             environment {
                  CI = 'true'
                  scannerHome = tool 'devops'
            }
            steps {
                script {
                    gv = load "script.groovy"
                }
            }
        }
        stage("SonarQube Testing and Scan") {

            steps {
                script {
                    gv.sonarScan()
                }
            }
        }
       stage("Push JAR to Nexus"){
            steps {
                script {
                    gv.pushToNexus()
                }
            }
       }
    }
}