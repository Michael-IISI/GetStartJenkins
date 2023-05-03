pipeline {
    agent any

    stages {
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
       stage('Cat README.md'){
           when {
               branch "fix-*" 
           }
           steps {
               sh '''
                  cat README.md
               '''
           }
       }
    }
}
