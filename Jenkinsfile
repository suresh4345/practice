pipeline{
    
    agent any 

    stages {
        
        stage('Git Checkout'){
            
            steps{
                
                script{
                    
                  //  git branch: 'main', url: 'https://github.com/vikash-kumar01/mrdevops_javaapplication.git'
                  git branch: 'main', url: 'https://github.com/suresh4345/practice.git'
                }
            }
        }
       stage('UNIT testing'){
            
           steps{
                
               script{

                    sh 'mvn test'
                }
            }
        }
      
        stage('Integration testing'){
        
            steps{
                
                script{
                    
                    sh 'mvn verify -DskipUnitTests'
                }
            }
        }
        stage('Maven build'){
            
            steps{
                
                script{
                    
                    sh 'mvn clean install'
                }
            }
        }
        stage('Static code analysis'){
            
            steps{
                
                script{
                    
                    withSonarQubeEnv(credentialsId: 'sonar key') {
                        
                        sh 'mvn clean package sonar:sonar'
                    }
                   }
                    
                }
            }
            // stage('Quality Gate Status'){
                
            //     steps{
                    
            //         script{
                        
            //           waitForQualityGate abortPipeline: false, credentialsId: 'sonar key'
            //         }
            //     }
            // }


            stage('copy jar file to nexus repo'){

                    steps{

                            script{
                                def readPomVersion = readMavenPom file: 'pom.xml'
                                    nexusArtifactUploader artifacts: [
                                        [artifactId: 'springboot', 
                                        classifier: '', 
                                        file: 'Uber.jar', 
                                        type: 'jar']
                                        ], 
                                        credentialsId: 'nexus-auth', 
                                        groupId: 'com.example', 
                                        nexusUrl: 'http://localhost:8081/', 
                                        nexusVersion: 'nexus3', 
                                        protocol: 'http', 
                                        repository: 'demoapp_release', 
                                        version: '${readPomVersion.version}'

                            }


                    }



            }
        }
        
}