@Library("shared-library") _
pipeline {
    agent any
    stages {
        stage('Cat README.md'){
            steps {
               sh '''
                  cat README.md
               '''
           }
       }
       stage('Back-end') {
            agent {
                docker { image 'maven:3.9.0-eclipse-temurin-11' }
            }
            steps {
                sh 'mvn --version'
            }
        }
        stage('Front-end') {
            agent {
                docker { image 'node:18.16.0-alpine' }
            }
            steps {
                sh 'node --version'
            }
        }
        stage('Build') {
            agent {
                docker {
                    image 'gradle:6.7-jdk11'
                    // Run the container on the node specified at the
                    // top-level of the Pipeline, in the same workspace,
                    // rather than on a new node entirely:
                    reuseNode true
               }
            }
            steps {
                echo 'Building..'
                sh 'gradle --version'
            }
        }
        stage('Test') {
            steps {
                echo 'Docker Testing..'
                sh ''' node --version'''
                sh 'node --version'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
        stage('Example') {
            steps {
                echo "Running ${env.BUILD_ID} on ${env.JENKINS_URL}"
            }
        }
        stage('Shared-Library Variables') {
            steps {
                helloWorld(name:"Michael Li",dayOfWeek:"星期五 Friday")
            }
        }
    }
}
