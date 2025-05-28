pipeline {
    /*agent any*/
    agent {label 'devops'}
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
        stage ("k8s") {
            steps {
                sh "kubectl rollout restart deployment/java-app"
                }
            }
        }
}

        /*
        stage ("k8s") {
            steps {
                withEnv(["KUBECONFIG=/var/lib/jenkins/.kube/config"]) {
                    sh "kubectl rollout restart deployment/java-app"
                }
            }
        }


      /*  stage ("k8s"){
            steps {
                sh "export KUBECONFIG=/etc/kubernetes/admin.conf"
                sh "sudo kubectl rollout restart deployment/java-app"
                sh "sudo /usr/local/bin/kubectl rollout restart deployment/java-app"
           }
        }*/
    }
}
*/
