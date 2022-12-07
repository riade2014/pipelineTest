/*pipeline {
    environment {
        JAVA_TOOL_OPTIONS = "-Duser.home=/var/maven"
    }
    agent {
        docker {
            image "maven:3.8.6-jdk9"
            label "docker"
        
            args "-v /tmp/maven:/var/maven/.m2 -e MAVEN_CONFIG=/var/maven/.m2"
        }
    }

    stages {
        stage("Build") {
            steps {
                sh "mvn -version"
                sh "mvn clean install"
            }
        }
    }

    post {
        always {
            cleanWs()
        }
    }
}*/

pipeline{
    agent any
    
   tools {
        maven "maven" // You need to add a maven with name "3.6.0" in the Global Tools Configuration page
    }
    stages{
        stage('git checkout'){
            steps{
                 git credentialsId:'credentID',url:'https://github.com/riade2014/pipelineTest'
            }
        }
        stage('Build the application'){
            steps{
                bat' mvn clean install'
            }
        }
        stage('Unit Test Execution'){
            steps{
                 bat 'mvn test'
            }
        }
      stage('Build the image docker'){
          steps{
              bat 'docker build -t sylviane/maven-pipeline-demo .'
          }
      }
    }
}
