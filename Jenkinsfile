pipeline {
  agent any
  stages {
    stage("Checkout") {
      steps {
        git url: 'https://github.com/lintmint/calculator.git'
      }
   }
   stage("Compile") {
     steps {
      sh "./gradlew compileJava"
     }
    }
  }
} 
