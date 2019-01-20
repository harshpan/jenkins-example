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
                    sh 'mvn deploy'
                }
            }
       }
        
         stage ('BuildSlave') {

            steps {
                agent { 
                label 'slave'
            }
                withMaven(maven : 'localMaven')
            }
        }
    }
}
