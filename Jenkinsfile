pipeline{
  agent any
  tools{
        maven 'Maven'
  }
  stages{
        stage('Cleanup Workspace'){
              steps{
                cleanWs()
              }
        }
        stage('Checkout from SCM'){
               steps{
                 echo "Checking out for the Code from Github"
                 checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: 'MyGithubCreds', url: 'https://github.com/ddandeti/register-app']])
                 echo "Checkout done"
               }
        }
        stage('Build Application'){
                steps{
                  echo "Building the Application"
                  sh "mvn clean package install"
                  echo "Build done"
                }
        }
        stage('Test Application'){
                 steps{
                   echo "Tesing the Application"
                   sh "mvn test"
                   echo "Testing Done"
                 }
        }
  }
  
}
