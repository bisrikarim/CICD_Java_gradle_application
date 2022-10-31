pipeline{

    agent any

    stages{

        stage("sonar quality check"){

            steps{

                script{

                    withSonarQubeEnv(credentialsId: 'sonar-token') {


                        sh 'chmod +x gradlew'

                        sh './gradlew sonarqube'

                    }
                     timeout(time: 10, unit: ‘MINUTES’) {
              def qg= waitForQualityGate()
            if (qg.status!= ‘OK’){
                error “Pipeline aborted due to quality gate failure: ${qg.status}”
            }
        }         
              echo ‘Quality Gate Passed’

                }

            }

        }

    }

}

