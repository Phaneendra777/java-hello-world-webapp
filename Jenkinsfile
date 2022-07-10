pipeline {
    agent any
    tools{
        maven 'maven3'
    }
    stages{
        stage("Checkout stage") {
        steps{
            git 'https://github.com/Phaneendra777/java-hello-world-webapp.git'
        }
        }
        stage("Build-satage"){
            steps{
                sh 'mvn clean package'
                sh 'mv target/*.war target/demo.war'
            }
        }
        stage("deploy war file to tomcat"){
            steps{
                sshagent(['ec2-id']){
                    sh "scp -o StrictHostKeyChecking=no target/demo.war ubuntu@172.31.4.43:/var/lib/tomcat9/webapps"
                }
            }
        }
        }
}
