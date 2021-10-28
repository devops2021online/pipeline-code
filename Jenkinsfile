// this is code for deployment
pipeline {
    agent any
    stages {
        stage('Git Clone') {
            steps {
                git branch: 'master', url: 'https://github.com/devops2021online/java-maven-sample-war.git'
            }
        }
        stage('Maven Build') {
            steps {
                sh 'mvn clean package'
            }
        }
        stage('Tomcat Deploy') {
            steps {
                sshagent(['my-aws-creds']) {
                 sh 'scp -o StrictHostKeyChecking=no target/Example-0.0.1-SNAPSHOT.war ec2-user@172.31.2.45:/opt/apache-tomcat-9.0.54/webapps/'
                }
            }
        }
    }
}
