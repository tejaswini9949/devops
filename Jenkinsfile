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
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }
        stage('Deploy to tomcat server'){

            steps{
                
          deploy adapters: [tomcat9(credentialsId: 'tomcat', path: '', url: 'http://15.207.110.255:8080/')], contextPath: 'webapp', war: '**/*.war'     
                
            }
            
        }
        
     }
}

              
