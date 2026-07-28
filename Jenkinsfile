pipeline {

    agent { label 'docker' }

    environment {
        IMAGE = "website-image"
        CONTAINER = "website-container"
    }

    stages {

        stage('Clone') {
            steps {
                git 'https://github.com/adarshsharma206/beginner-html-site-styled'
            }
        }

        stage('Build Image') {
            steps {
                sh 'docker build -t $IMAGE .'
            }
        }

        stage('Remove Old Container') {
            steps {
                sh '''
                docker rm -f $CONTAINER || true
                '''
            }
        }

        stage('Run Container') {
            steps {
                sh '''
                docker run -d \
                --name $CONTAINER \
                -p 99:80 \
                $IMAGE
                '''
            }
        }

    }
}