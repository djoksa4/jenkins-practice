env.DOCKER_HOST = 'tcp://20.8.105.25:4243'

pipeline {
    agent {
        docker {
            image "maven:3.6.0-jdk-13"
            label "docker"
        }
    }


    stages {
        stage("Build") {
            steps {
                sh "mvn -version"
                sh "mvn clean install"
            }
        }
    }

    post {
        always {
            cleanWs()
        }
    }
}