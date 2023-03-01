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
    }
}
