node {
   def mvnHome
  stage('Prepare') {
      git url: 'https://github.com/kesavkummari/b78am.git', branch: 'jfrog'
      mvnHome = tool 'maven'
   }
  stage ('Code Scanning') {
      sh "'${mvnHome}/bin/mvn' sonar:sonar"
  }
  stage ('Clean') {
      sh "'${mvnHome}/bin/mvn' clean"
  }
  stage ('Validate') {
      sh "'${mvnHome}/bin/mvn' validate"
  }
  stage ('Compile') {
      sh "'${mvnHome}/bin/mvn' compile"
  }
  stage ('Test') {
      sh "'${mvnHome}/bin/mvn' test"
  }
  stage ('Package') {
      sh "'${mvnHome}/bin/mvn' package"
  }
  stage ('Verify') {
      sh "'${mvnHome}/bin/mvn' verify"
  }
  stage ('Install') {
      sh "'${mvnHome}/bin/mvn' install"
  }
  stage ('Install') {
      sh "'${mvnHome}/bin/mvn' deploy"
  }
  stage ('Deliver Artifact To Tomcat') {
      sh 'curl -u admin:redhat@123 -T target/**.war "http://3.95.200.169:8080/manager/text/deploy?path=/opswork&update=true"'
  }
  stage ('Smoke Test') {
      sh 'curl --retry-delay 10 --retry 5 "http://3.95.200.169:8080/opswork"'
  }
  
}
