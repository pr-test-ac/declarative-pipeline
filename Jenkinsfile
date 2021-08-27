//Declarative Pipeline syntax:

pipeline{
    agent any       //we can use none or any - means run pipeline on any node
    tools {
        maven 'maven3'
        jdk 'jdk11'
    }
    environment {
        MY_NAME='Pawan Rampal'
    }
    options {
        //These are the same that you see in the gui when you configure a project
        //https://www.jenkins.io/doc/book/pipeline/syntax/#options

        buildDiscarder(logRotator(numToKeepStr: '3')) 
    }
    parameters {
        //string boolean choice etc
        choice(name: 'DEPLOY_ENV', choices: ['Test', 'dev', 'uat'], 
        description: 'Select the env that you want to deploy:')
    }
    stages{
        stage('Compile'){
            steps {
                sh 'mvn compile'
            }
        }
        stage('Test'){
            steps{
                sh 'mvn test'
            }
        }
        stage('Package'){
            steps{
                sh 'mvn package'
            }
       }
        stage('Archive Artifact'){
            steps{
                archiveArtifacts artifacts: 'target/*.jar', followSymlinks: false
            }
        }
    }
}
