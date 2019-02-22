pipeline {
    agent any
    stages{
        stage('Build'){
           steps {
              echo 'Building...'
              bat 'mvn clean package'
           }
            post{
                success{
                    echo 'Now Archiving...'
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }
        stage('Deploy to Staging'){
            steps{
              build job:'deploy_to_staging'
            }
        }
    }
}
