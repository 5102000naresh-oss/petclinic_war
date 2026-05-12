pipeline{
  agent any

  triggers {
    githubPush()
  }

  stages{

    stage('git'){

      steps{

        git branch:'main',
        url:'https://github.com/5102000naresh-oss/petclinic_war.git'
      }
    }

    stage('build'){

      steps{

        sh 'mvn clean package'
      }
    }
  }
}
