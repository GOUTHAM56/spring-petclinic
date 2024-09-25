pipeline {
  agent any
  stages {
    stage('Compile') {
      steps {
        sh './mvnw clean compile'
      }
    }

    stage('Static Analysis') {
      steps {
        sh '''mvn sonar:sonar \\
  -Dsonar.projectKey=Petclinic \\
  -Dsonar.projectName=\'Petclinic\' \\
  -Dsonar.host.url=https://172.31.28.164:9000 \\
  -Dsonar.token=sqp_541d387979c1aedc118c079cee451452121f8fe8'''
      }
    }

  }
}