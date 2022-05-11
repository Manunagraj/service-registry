#!/usr/bin/env groovy

node('maven') {

    // default Java version
    sh "java -version"
    


stage('Checkout') {
    
        try {
             checkout([$class: 'GitSCM', branches: [[name: '*/master']],
             userRemoteConfigs: [[url: 'https://github.com/Manunagraj/service-registry.git']]])
        } catch (Exception error) {
            notifyStash("FAILED")
            throw error
        }
    }
 

     stage('Maven Build') {
      withMaven(maven: 'mvn') {
            sh "mvn clean package"
        }
    }
}
