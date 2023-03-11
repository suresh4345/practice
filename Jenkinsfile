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
       stage('MAVEN install'){
            
           steps{
                
               script{
                    
                   sh 'mvn clean install'
              }
           }
       }
        // stage('Integration testing'){
            
        //     steps{
                
        //         script{
                    
        //             sh 'mvn verify -DskipUnitTests'
        //         }
        //     }
        // }
        // stage('Maven build'){
            
        //     steps{
                
        //         script{
                    
        //             bat 'mvn clean install'
        //         }
        //     }
        // }
        // stage('Static code analysis'){
            
        //     steps{
                
        //         script{
                    
        //             withSonarQubeEnv(credentialsId: 'sonar-api') {
                        
        //                 sh 'mvn clean package sonar:sonar'
        //             }
        //            }
                    
        //         }
        //     }
            // stage('Quality Gate Status'){
                
            //     steps{
                    
            //         script{
                        
            //             waitForQualityGate abortPipeline: false, credentialsId: 'sonar-api'
            //         }
            //     }
            // }
        }
        
}
