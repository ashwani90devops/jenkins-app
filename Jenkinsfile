node {
   // Defining variable	
   // def sonarUrl = 'sonar.host.url=http://192.168.1.16:9000'
   // def mvn = tool (name: 'maven-jenkins', type: 'maven') + '/bin/mvn'
   
   stage('SCM Checkout'){
          // Clone repo
          git branch: 'main', 
	  credentialsId: 'ashwani90devops', 
	  url: 'https://github.com/ashwani90devops/jenkins-app'
   
   }
		
   stage('MVN Package'){
	  // Build using maven
	  sh "mvn clean package"
   }

   stage('Email Notification'){
          // Send Email Notification
          mail bcc: '', body: '''Hi

Welcome to Jenkins email alerts

Thanks,
Ashwani''', cc: '', from: '', replyTo: '', subject: 'Jenkins Job', to: 'ashwani90devops@gmail.com'
   }

}
