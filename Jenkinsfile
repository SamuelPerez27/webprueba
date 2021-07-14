pipeline {
    agent any

    stages {
        stage('clean') {
            steps {
              bath "rmdir /s /q webprueba"
              bath "git clone https://github.com/SamuelPerez27/webprueba.git"
              bat "mvn clean -f webprueba"
             
            }
        }
           stage('install') {
            steps {
                  bat "mvn install -f webprueba"
            }
        }
        
        stage('Test') {
            steps {
                bat "mvn test -f webprueba"
            }
        }
        
        stage('Package') {
            steps {
                    bat "mvn package -f webprueba"
            }
        }
    }

    post{
       
       always{
           emailext body: 'Saludos', subject: 'Pipeline Failed Jenkins', to: 'samuelpperez07@gmail.com'
       }
    }
}
