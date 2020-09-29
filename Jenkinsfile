pipeline{

 agent any

stages{
	
 stage('Git Clone SourceCode'){

 steps{

 git 'https://github.com/Neikl/salesforce-app-mig.git'

 }

 }

 stage('Running ANT scripts'){

 steps{

 sh "ant retrieveUnpackaged -v && ant deployUnpackaged -v"

 }

 }

 stage('Production Server status'){

 steps{

 sh "curl -s --head  --request GET  https://saas-inspiration-5803-dev-ed.cs6.my.salesforce.com | grep '200'"

 }

 }	
	
 stage('Chatter Notifier'){

 steps{

 chatterPost body: "This is a Chatter post from a pipeline! ${env.JOB_NAME} ${env.BUILD_DISPLAY_NAME}", credentialsId: 'team.sfdc.user'

 }

 } 
 
 }

 }
