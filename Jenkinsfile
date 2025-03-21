pipeline {
  agent any
  stages {
    stage('Maven Version') {
      steps {
        sh 'echo Print Maven Version'
        sh 'mvn -version'
      }
    }

    stage('Build') {
      steps {
        sh 'mvn clean package -DskipTests=true'
        archiveArtifacts 'target/hello-demo-*.jar'
      }
    }

    stage('Test') {
      steps {
        sh 'mvn test'
        junit(testResults: 'target/surefire-reports/TEST-*.xml', keepProperties: true, keepTestNames: true)
      }
    }
    
    stage('Local Deployment') {
      steps {
        sh """ java -jar target/hello-demo-*.jar > /dev/null & """
      }
    }
    
    stage('Integration Testing') {
      steps {
        sh 'sleep 5s'
        sh 'curl -s http://localhost:6767/hello'
      }
    }


  }
  tools {
    maven 'M398'
  }

}
