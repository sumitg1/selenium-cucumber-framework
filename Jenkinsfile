pipeline {
     agent any
 
     tools {
         maven 'MAVEN_HOME'
      }
 
     stages {
 
         stage('Checkout') {
             steps {
                 checkout scm
                 stash 'src'
             }
         }
 
         stage('Run tests') {
             steps {
                 parallel branch1: {
                     node('master') {
                         unstash 'src'
                         bat 'mvn --batch-mode -V -U -e clean test -Dsurefire.useFile=false -Dcucumber.options=\"--plugin json:target/cucumber-branch1.json \"'
                         cucumber fileIncludePattern: '**/cucumber-*.json', parallelTesting: true
                     }
                 }, branch2: {
                     node('master') {
                         unstash 'src'
                         bat 'mvn --batch-mode -V -U -e clean test -Dsurefire.useFile=false -Dcucumber.options=\"--plugin json:target/cucumber-branch2.json\"'
                         cucumber fileIncludePattern: '**/cucumber-*.json', parallelTesting: true
                     }
                 }
             }
         }
     }
  }
