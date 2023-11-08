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
        
          sh """
          aws ecr get-login-password --region us-east-1 | docker login --username AWS --password-stdin 852068596012.dkr.ecr.us-east-1.amazonaws.com
          docker build -t frontendapp .
          docker tag frontendapp:latest 852068596012.dkr.ecr.us-east-1.amazonaws.com/san-test-ecr:latest
          docker push 852068596012.dkr.ecr.us-east-1.amazonaws.com/san-test-ecr:latest
          """
        }
      }
    }
  }