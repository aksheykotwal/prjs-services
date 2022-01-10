# prjs-services
Project Micro Service


node('nodejs') { 
 stage('Checkout') { 
 git url: 'https://github.com/YOUR_GITHUB_USER/DO400-apps', branch:
 'scripted-pipelines'
 }
 stage('Test') { 
 sh 'node ./simple-webapp/backend/test.js'
 sh 'node ./simple-webapp/frontend/test.js'
 }
}




-----
pipeline {
 agent any
 stages {
 stage('Checkout') {
 steps {
 git branch: 'main', url: 'https://github.com/RedHatTraining/DO400-
apps'
 }
 }
 stage('Test Word Count') {
 steps {
 sh './story-count/test-wc.sh ./story-count/frankenstein.txt 500'
 }
 }
 }
}


