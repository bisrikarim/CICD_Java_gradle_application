pipeline{
    agent any
        
    stages{
        stage("sonar quality check"){
            agent {
                docker {
                    image 'openjdk:latest'
                }
            }
            steps{
                script {
                    withSonarQubeEnv(credentialsId: 'sonar-token') 
                    {
                            sh 'chmod +x gredlew'
                            sh './gradlew sonarqube'
                    }

                }
            }
          
        }
    }
}
