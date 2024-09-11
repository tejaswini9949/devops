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
              post{

                success{

                    echo "Archiving the Artifacts"
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }







         
        }

stage('DEPLOY') {
            steps {
                

        deploy adapters: [tomcat9(credentialsId: 'tomcat', path: '', url: 'http://15.207.110.255:8080/')], contextPath: 'javaapp', war: '**/*.war'            

     
   }
 }


        
     }
}
