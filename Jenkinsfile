pipeline {
    agent any 
    tools {
         maven 'maven'
         jdk 'java'
    }
    stages {
       stage('Stage-0 : Static Code Quality Using SonarQube') { 
            steps {
                sh 'mvn sonar:sonar' 
            }
        }
        stage('Stage-1 : Clean') { 
            steps {
                sh 'mvn clean'
            }
        }
         stage('Stage-2 : Validate') { 
            steps {
                sh 'mvn validate'
            }
        }
         stage('Stage-3 : Compile') { 
            steps {
                sh 'mvn compile'
            }
        }
         stage('Stage-4 : Test') { 
            steps {
                sh 'mvn test'
            }
        }
          stage('Stage-5 : Install') { 
            steps {
                sh 'mvn install'
            }
        }
          stage('Stage-6 : Verify') { 
            steps {
                sh 'mvn verify'
            }
        }
          stage('Stage-7 : Package') { 
            steps {
                sh 'mvn package'
            }
        }
        stage('Stage-8 : Push an Artifact to Artifactory Manager i.e. AWS CodeArtifact/S3/Nexus/Jfrog') { 
            steps {
                sh 'mvn deploy'
            }
        }
        stage('Stage-9 : Deliver the Artifact to Tomcat cloudbinary-5.0.0.war file to Tomcat Server') { 
            steps {
                sh 'curl -u admin:redhat@123 -T target/**.war "http://54.160.172.218:8080/manager/text/deploy?path=/opswork&update=true"'
            }
        } 
        stage('Stage-10 : SmokeTest') { 
            steps {
                sh 'curl --retry-delay 10 --retry 5 "http://54.160.172.218:8080/opswork"'
            }
        }
    }
}
