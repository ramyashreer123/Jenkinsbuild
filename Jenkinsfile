node {
   def M2_HOME
   stage('getscm') { // for display purposes
      // Get some code from a GitHub repository
      git 'https://github.com/chetanshell/Jenkinsbuild.git'
      // Get the Maven tool.
      // ** NOTE: This 'M3' Maven tool must be configured
      // **       in the global configuration.           
      M2_HOME = tool 'maven'
   }
   stage('Build') {
      // Run the maven build
      if (isUnix()) {
           sh "'${M2_HOME}/bin/mvn' -Dmaven.test.failure.ignore clean package"
         //sh "`${M2_HOME}/bin/mvn` package"
      } else {
      echo 'this is build maven artifact'
         bat(/"${M2_HOME}\bin\mvn" -Dmaven.test.failure.ignore package/)
      }
   }
   stage ('Testing Stage') {

            steps {
                withMaven(maven : 'M2_HOME') {
                    sh 'mvn test'
                }
            }
        }
   stage ('deploy'){
   echo 'deployment started'
       sh "cp /var/lib/jenkins/workspace/${ITEM_FULL_NAME}/target/*.war /root/apache-tomcat-8.5.54/webapps"
   }
}
