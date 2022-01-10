# prjs-services
Project Micro Service

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


