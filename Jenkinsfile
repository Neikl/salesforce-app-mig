pipeline{

 agent any

stages{
	
 stage('Check out source'){

 steps{

 checkout scm

 }

 }

 stage('Retrieving Metadata'){

 steps{

 sh "ant retrieveUnpackaged -v"

 }

 }
	
 stage('Depoying to QA'){

 steps{

 sh "ant deployUnpackaged -v"

 }

 }

 stage('QA Server status'){

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
