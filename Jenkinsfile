pipeline {
    agent any
   tools{
        maven 'maven'
    
     }

    stages {
        stage('CLONE') {
            steps {
                
          git credentialsId: 'Git', url: 'https://github.com/tejaswini9949/devops.git'
            }
        }
     stage('BUILD') {
            steps {
                sh "mvn clean package"
            }
        }

stage('DEPLOY') {
            steps {
                sshagent(['tom']) {

         sh "scp -o StrictHostKeyChecking=no target/vansro-1.0-SNAPSHOT.jar  ec2-user@15.207.110.255:/opt/tomcat/webapps"

                    

     }
   }
 }


        
     }
}
