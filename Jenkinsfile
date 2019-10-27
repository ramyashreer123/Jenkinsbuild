node {
   def mvnHome
   stage('getscm') { // for display purposes
      // Get some code from a GitHub repository
      git 'https://github.com/chetanshell/Jenkinsbuild.git'
      // Get the Maven tool.
      // ** NOTE: This 'M3' Maven tool must be configured
      // **       in the global configuration.           
      mvnHome = tool 'Maven'
   }
   stage('Build') {
      // Run the maven build
      if (isUnix()) {
         sh "'${mvnHome}/bin/mvn' -Dmaven.test.failure.ignore clean package"
      } else {
      echo 'this is build maven artifact'
         bat(/"${mvnHome}\bin\mvn" -Dmaven.test.failure.ignore clean package/)
      }
   }
   stage ('deploy'){
   echo 'deployment started'
       sh label: '', script: 'cp /var/lib/jenkins/workspace/"${env.JOB_NAME}"/target/*.war /opt/apache-tomcat-8.5.47/webapps'
   }
}
