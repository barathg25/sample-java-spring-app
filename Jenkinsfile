pipeline {
    agent any
    stages{
        stage ("clone") {
            steps {
                git branch: 'master', url: 'https://github.com/barathg25/sample-java-spring-app.git'
            }
        }
        stage ("build") {
            steps {
                sh "mvn clean install"
            }
        }
        stage ("docker image"){
            steps {
                sh "docker build -t barathg25/java ."
                sh "docker images"
            }
        }
        stage("docker hub") {
            steps {
                sh "docker login -u barathg25 -p barath@12345"
                sh "docker push barathg25/java"
            }
        }
        stage ("docker conatainer"){
            steps {
                sh "docker rm -f java"
                sh "docker run -d --name java -p 8087:8080 barathg25/java"
            }
        }
    }
}
