pipeline {
    agent any
    options {
        skipStagesAfterUnstable()
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
                    def customImage = docker.build("demo.goharbor.io/backstage/busybox:${env.BUILD_ID}")
                }
            }
        }

        stage('Publish') {
            steps{
                script {
                    docker.withRegistry('https://demo.goharbor.io', harbor) {
                        customImage.push()
                    }
                }
            }
        }
    }
}
