pipeline {
    agent any
    stages {
        stage('Clone stage') {
            steps {
                git credentialsId: 'ssh-gitlab', url: 'git@gitlab-ssh.whiteskylabs.com:mark.ortiz/specter-cache-system-api.git'
            }
        }
        stage('Build and Test') {
            steps {
                sh '/var/jenkins_home/apache-maven-3.6.3/bin/mvn clean test'
            }
        }
        stage('Publish Munit'){
            steps {
                publishHTML([allowMissing: false, alwaysLinkToLastBuild: false, keepAll: false, reportDir: '\\target\\site\\munit\\coverage', reportFiles: 'summary.html', reportName: 'Code Coverage', reportTitles: ''])
            }
        }
        stage('Sonarqube') {
            steps {
                sh '/var/jenkins_home/apache-maven-3.6.3/bin/mvn sonar:sonar'
            }
        }
        stage('Deployment') {
            steps {
                sh '/var/jenkins_home/apache-maven-3.6.3/bin/mvn -X deploy -DmuleDeploy -Dmaven.test.skip=true -Dmaven.install.skip=true'
            }
        }
    }    
}