pipeline{
  agent any
  stages{
    stage("git version"){
      steps{
        sh "git --version"
      }
    }
    stage("mvn version"){
      steps{
        sh "mvn --version"
      }
    }
    stage("docker version"){
      steps{
        sh "docker --version"
      }
    }
  }
}