pipeline {

agent any

stages
{

stage('cloning code')

{

steps

{git 'https://github.com/chaitanyapratap19/maven-project.git'
}
}

stage('compile my project')
{
steps
{
withMaven(jdk: 'localJDK', maven: 'localMaven') {
    sh 'mvn compile'
}}}
    
stage('test my project')
{
steps
{
withMaven(jdk: 'localJDK', maven: 'localMaven') {
    sh 'mvn test'
}}}
    
stage('package my project')
{
steps
{
withMaven(jdk: 'localJDK', maven: 'localMaven') {
    sh 'mvn package'
}}}
    

    
        
stage('package my install')
{
steps
{
withMaven(jdk: 'localJDK', maven: 'localMaven') {
    sh 'mvn install'
}}}
    
stage('deploy to  tomcat')
{
steps
{
    sshagent (['3.18.213.59']) {
	 sh 'scp -o StrictHostKeyChecking=no */target/*.war ec2-user@3.18.213.59:/var/lib/tomcat/webapps'
						}
}
}
    
    
    

}
}
