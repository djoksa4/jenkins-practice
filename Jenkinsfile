pipeline {
    environment {
        JAVA_TOOL_OPTIONS = "-Duser.home=/home/jenkins"
    }

    agent {
        dockerfile {
            args "-v /tmp/maven:/home/jenkins/.m2 -e MAVEN_CONFIG=/home/jenkins/.m2 -u root:root"
        }
    }


    stages {
        stage("Build") {
            steps {
                sh "mvn -version"
                sh "mvn clean install"
            }
        }

        stage("Run") {
            steps {
                sh "java -jar /var/lib/jenkins/workspace/jenkins_docker_maven_pipeline/target/java-project2-1.0-SNAPSHOT.jar"  
            }
        }
    }


    post {
        always {
            cleanWs()
        }
    }
}