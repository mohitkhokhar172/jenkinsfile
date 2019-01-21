node {
    
    stage ('checkout'){
        
    git 'https://github.com/nitinrocksss/JenkinsTest.git'
        
        }
    stage('mvn package'){
    
    def maven_home= tool name: 'MAVEN_HOME', type: 'maven'
    def mvn_cmd = "${maven_home}/bin/mvn"
    "${mvn_cmd} mvn package"
    }
   
    stage('email notification')
    {
        mail bcc: '', body: 'Hello', cc: '', from: 'nitinarorayv@gmail.com', replyTo: '', subject: 'job from jenkins', to: 'nitinarorayv@gmail.com'
    
     }
    
    stage('SonarQube Analysis') {
        def mvnHome =  tool name: 'MAVEN_HOME', type: 'maven'
       
        withSonarQubeEnv('sonar-7.5') { 
             withCredentials([usernameColonPassword(credentialsId: '87e3d577-1764-48e9-ba70-4afb756a9b29', variable: 'password')]) {
         
   
            "${mvnHome}/bin/mvn  sonar:sonar"
           
    }
      }
}
         }
    
