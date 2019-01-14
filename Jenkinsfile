pipeline {
  agent any
  triggers {
    pollSCM('* * * * *')
  }

  stages {
    stage("Compile") {
      steps {
        sh "./gradlew compileJava"
      }
    }
   stage("Unit test") {
      steps {
        sh "./gradlew test"
      }
    }
   stage("Build") {
      steps {
        sh "./gradlew build"
      }
   }
   stage("Docker build") {
      steps {
        sh "docker build -t calculator ."
     }
   }
   stage("Docker push") {
      steps {
        sh "docker push localhost:5000/calculator}"
      }
   }
 }
}
