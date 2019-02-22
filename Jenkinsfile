
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
        stage ('Deploy to Production'){
            steps{
                timeout(time:5, unit:'DAYS'){
                input message:'Approve PRODUCTION Deployment?'
                }
                build job: 'deploy_to_prod'
            }
            post {
                success {
                    echo 'Code deployed to Production.'
                }
                failure {
                    echo ' Deployment failed.'
                }
            }
        }
    }
}
