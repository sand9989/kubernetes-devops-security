pipeline{
  agent any
  stages{
    stage("git code checkout"){
      steps{
        cleanWs()
        git branch: 'main', credentialsId: 'Jenkins-cred', url: 'https://github.com/sand9989/kubernetes-devops-security.git'
      }
    }
    stage("mvn package"){
      steps{
        sh "mvn clean package -DskipTests=true"
      }
    }
    stage("mvn test"){
      steps{
        sh "mvn test"
      }
      post{
        always{
          junit 'target/surefire-reports/*.xml'
          jacoco execPattern: 'target/jacoco.exec'
        }
      }
    }

    stage("docker image creation"){
      steps{
        dir('/var/lib/jenkins/docker'){
          sh "sudo docker build -t frontendapp ."
        }
        
      }
    }
  }
}