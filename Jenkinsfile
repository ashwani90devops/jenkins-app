node {
   // Defining variable	
      def sonarUrl = 'sonar.host.url=http://192.168.1.63:9000'
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

   stage('SonarQube Analysis'){
           withSonarQubeEnv('sonar') {
             sh "mvn sonar:sonar"
	 }
   }	

   stage('Email Notification'){
          // Send Email Notification
          mail bcc: '', body: '''Hi

Welcome to Jenkins email alerts ASHWANI007

Thanks,
Ashwani''', cc: '', from: '', replyTo: '', subject: 'Jenkins Job', to: 'ashwani90devops@gmail.com'
   }
   
   stage('Slack Notification'){
          // Send Slack Notification
          slackSend baseUrl: 'https://hooks.slack.com/services/', channel: '#jenkins-ashwani-devops', color: 'good', failOnError: true, message: 'Welcome To Jenkins Slack', teamDomain: 'ashwani90devops', tokenCredentialId: 'SlackToken'
   }
}
