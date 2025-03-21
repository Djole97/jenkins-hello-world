pipeline {
    agent any

    tools {
        // Install the Maven version configured as "M3" and add it to the path.
        maven "M399"
    }

    stages {
        stage('Echo Version'){
            steps{
             sh 'echo Print Maven Version'
             sh 'mvn -version'
            }
        }
         stage('Build') {
            steps {
                // Get some code from a GitHub repository
                // git branch: 'main', changelog: false, poll: false, url: 'https://github.com/Djole97/jenkins-hello-world'
                
                // Run Maven Clean package
                sh "mvn clean package -DskipTests=true"

            }
         }
         stage('Unit Test'){
             steps {
                 sh "mvn test"
             }
           }
           
         }
    }
