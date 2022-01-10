# prjs-services
Project Micro Service


node('nodejs') {
 stage('Checkout') {
 git url: 'https://github.com/YOUR_GITHUB_USER/DO400-apps', branch:
 'scripted-pipelines'
 }
 stage('Test') {
 if (isChanged('simple-webapp/backend')) {
 echo 'Detected Backend changes'
 sh 'node ./simple-webapp/backend/test.js'
 }
 if (isChanged('simple-webapp/frontend')) {
 echo 'Detected Frontend changes'
 sh 'node ./simple-webapp/frontend/test.js'
 }
 }
}
def isChanged(dir) {
 changedFilepaths = sh(
 script: 'git diff-tree --no-commit-id --name-only -r HEAD',
 returnStdout: true
 ).trim().split('\n')
 for (filepath in changedFilepaths) {
 if (filepath.startsWith(dir)) {
 return true;
 }
 }
 return false
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


