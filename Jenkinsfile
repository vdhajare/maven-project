
pipeline {
    agent any
    stages{
        stage('Build'){
           steps {
              echo 'Building...'
              bat 'mvn clean package'
               bat 'docker build . -t tomcatwebapp'
           }
            
        }      
    }
}
