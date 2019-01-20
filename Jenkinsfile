pipeline {
    agent any

    stages {
        stage ('Compile Stage') {

            steps {
                withMaven(maven : 'localMaven') {
                    sh 'mvn clean compile'
                }
            }
        }

        stage ('Testing Stage') {

            steps {
                withMaven(maven : 'localMaven') {
                    sh 'mvn test'
                }
            }
        }


        stage ('Deployment Stage') {
            steps {
                withMaven(maven : 'localMaven') {
                    sh 'mvn install'
                }
            }
       }
        
         stage ('BuildSlave') {

            steps {
                agent { 
                label 'Slave'
            }
                withMaven(maven : 'localMaven') {
                 
                     sh 'mvn install'
                    
                }
            }
        }
    }
}
