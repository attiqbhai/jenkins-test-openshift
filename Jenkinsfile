pipeline {
    agent any
    tools {
        jdk 'openjdk-8'
        maven '3.8.7'
    }
    environment {
        BUILD_VERSION = "v${currentBuild.number}.RELEASE"
    }
    stages {
        stage('check source') {
            steps {
                echo 'Hello World'
                git branch: 'main', url: 'https://github.com/attiqbhai/jenkins-test-openshift'
            }
        }
        stage('compile maven') {
            steps {
                echo 'Hello World'
                configFileProvider([configFile(fileId: 'maven-settings', variable: 'MAVEN_SETTINGS')]) {
                    sh "mvn clean package -s $MAVEN_SETTINGS"
                }
            }
        }
        stage('deploy to nexus') {
            steps {
                echo 'Hello World'
                configFileProvider([configFile(fileId: 'maven-settings', variable: 'MAVEN_SETTINGS')]) {
                    sh "mvn clean deploy -DaltDeploymentRepository=nexus::default::http://localhost:8081/repository/maven-snapshots/ -s $MAVEN_SETTINGS"
                }
            }
        }
    }
}