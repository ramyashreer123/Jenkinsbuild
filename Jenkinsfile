node {
   def M2_HOME
   stage('getscm') { // for display purposes
      // Get some code from a GitHub repository
      git 'https://github.com/chetanshell/Jenkinsbuild.git'
      // Get the Maven tool.
      // ** NOTE: This 'M3' Maven tool must be configured
      // **       in the global configuration.           
      M2_HOME = tool 'Maven'
   }
   stage('Build') {
      // Run the maven build
      if (isUnix()) {
         sh "'${M2_HOME}/bin/mvn' -Dmaven.test.failure.ignore clean package"
      } else {
      echo 'this is build maven artifact'
         bat(/"${M2_HOME}\bin\mvn" -Dmaven.test.failure.ignore clean package/)
      }
   }
   stage ('deploy'){
   echo 'deployment started'
       sh label: '', script: 'sudo cp /var/lib/jenkins/workspace/newpipeline/target/*.war /opt/apache-tomcat-8.5.47/webapps'
   }
}
