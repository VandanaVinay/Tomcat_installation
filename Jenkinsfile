pipeline {
    agent {
        label "tomcat"        
    }
    stages {
        stage('clone') {
            steps {
                sh 'rm -rf Automation'
                sh 'git clone https://github.com/VandanaVinay/hello-world-war.git'
            }
        }
        stage('Tomcat Install and Configuration') {
            steps {
                sh 'echo installing tomcat server....'
                sh 'chmod 755 ${WORKSPACE}/Tomcat_installation/Jenkinsfile'
                sh '${WORKSPACE}/Tomcat_installation/Jenkinsfile'
                sh 'echo installed the tomcat server succesfully....'
            }
        }
        stage('codeclone') {
            steps {
                sh 'rm -rf hello-world-war'
                sh 'git clone https://github.com/VandanaVinay/hello-world-war.git'
            }
        }
        stage('build') {
            steps {
                dir('hello-world-war') {
                sh 'mvn  package'
                }
            }
        }
        stage('build deploy') {
            steps {
                sh 'sudo cp ${WORKSPACE}/hello-world-war/target/hello-world-war-1.0.0.war /var/lib/tomcat9/webapps'
             
            }
       }
    }
}
