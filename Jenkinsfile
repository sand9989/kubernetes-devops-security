pipeline{
  agent any
  stages{
    stage("git code checkout"){
      steps{
        cleanWs()
        git branch: 'main', credentialsId: 'Jenkins-cred', url: 'https://github.com/sand9989/kubernetes-devops-security.git'
      }
    }
    stage("mvn test"){
      steps{
        sh "mvn package -DskipTests=true"
      }
    }
    stage("docker version"){
      steps{
        sh "docker --version"
      }
    }
  }
}