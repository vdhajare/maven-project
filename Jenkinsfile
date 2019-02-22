pipeline {
    agent any
    stages{
        stage('Build'){
           steps {
              echo 'Building...'
              bat 'mvn clean package'
              emailext body: 'test body', recipientProviders: [developers()], subject: 'test', to: 'vdhajare@gmail.com' 
            }
            
          }
    }
}
