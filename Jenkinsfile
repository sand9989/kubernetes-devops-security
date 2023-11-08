pipeline{
  agent any
  stages{
    stage("git code checkout"){
      steps{
        git branch: 'main', credentialsId: 'Jenkins-cred', url: 'https://github.com/sand9989/kubernetes-devops-security.git'
      }
    }
    stage("mvn test"){
      steps{
        cleanWs()
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