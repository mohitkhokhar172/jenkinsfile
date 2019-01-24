node{

    
   stage ('checkout'){
        
    git 'https://github.com/nitinrocksss/JenkinsTest.git'
        
        }
      
    stage('mvn package'){
    def mvn_version = 'mvn'
    withEnv( ["PATH+MAVEN=${tool mvn_version}/bin"] ) {
  //sh "mvn clean package"
    def maven_home= tool name: 'maven', type: 'maven'
   bat "mvn package"
    }
    }
    stage('email notification')
    {
        mail bcc: '', body: 'Hello', cc: '', from: 'nitinarorayv@gmail.com', replyTo: '', subject: 'job from jenkins', to: 'nitinarorayv@gmail.com'
    
     }
    
    stage('SonarQube Analysis') {
        def mvnHome =  tool name: 'MAVEN_HOME', type: 'maven'
         def mvn_cmd = "${mvnHome}/bin/mvn"
     def sonarhome = tool name: 'sonar-7.5', type: 'hudson.plugins.sonar.SonarRunnerInstallation'  
        withSonarQubeEnv('sonar-7.5') { 
             
             withCredentials([usernameColonPassword(credentialsId: '87e3d577-1764-48e9-ba70-4afb756a9b29', variable: 'password')]) {
         
   
          bat " ${mvn_cmd}  mvn sonar:sonar"
           
    }
      }
}
         }
    
