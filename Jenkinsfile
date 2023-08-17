pipeline {
    agent any
    triggers { pollSCM('*/2 * * * *')}
    stages{
        stage('Getting/cloning code from github'){
           steps{
               git 'https://github.com/mmislamqa88/hello-world.git'
           }
        
        }
        
        stage('Packaging the code'){
            steps{
                sh 'mvn package'
            }
        }
        
        stage('Deploying to the tomcat server'){
            steps{
                sshagent(['myKey']) {
                    sh "scp -o StrictHostKeyChecking=no webapp/target/webapp.war ubuntu@172.31.89.64:/opt/tomcat/apache-tomcat-10.1.11/webapps"
    
                }
            }
        }
        
    }
}
