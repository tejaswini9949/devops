pipeline{
    agent any
    tools{
        maven 'maven'
    
     }
     stages{
        stage("clone code"){
            steps{
              git credentialsId: 'git_credentials', url:'https://github.com/tejaswini9949/devops.git'
                
                
                            }


        }
        stage('Build'){

            steps{

                sh 'mvn clean install'
            }
            post{

                success{

                    echo "Archiving the Artifacts"
                    archiveArtifacts artifacts: '**/target/*.jar'
                }
            }
        }
        stage('Deploy to tomcat server'){

            steps{
                sshagent(['tom']) {
          sh "scp -o StrictHostKeyChecking=no target/vansro-1.0-SNAPSHOT.jar ec2-user@15.207.110.255:/opt/tomcat/webapps"     
                
                  }
            }
            
        }
        
     }
}

              
