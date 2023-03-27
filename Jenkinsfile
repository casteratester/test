pipeline {
    agent any
    options {
        skipStagesAfterUnstable()
    }
    environment {
        customImage = ''
    }

    stages {

       stage ('Say Hello') {
            steps {
                sh '''
                    echo "Hello"
                '''
            }
        }

        stage ('Build') {
            steps {
                script {
                    customImage = docker.build("demo.goharbor.io/backstage/busybox:${env.BUILD_ID}")
                }
            }
        }

        stage('Publish') {
            steps{
                script {
                    docker.withRegistry( 'https://demo.goharbor.io', 'harbor' ) {
                        customImage.push()
                    }
                }
            }
        }
    }
}
