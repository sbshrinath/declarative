pipeline {
        agent any

       stages {
            stage('Checkout') {
                steps {
                        checkout changelog: false, poll: false, scm: scmGit(branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/sbshrinath/declarative.git']])
                      }
                               }

            stage('Build') {
                steps {
                        sh '/home/remote/Documents/software/apache-maven-3.9.6/bin/mvn install'
                      }
                            }
            stage('Deployment') {
                steps {
                        sh 'cp target/declarative.war /home/remote/Documents/software/apache-tomcat-9.0.86/webapps'
                      }
                                }
            stage('Email notify') {
                steps {
                        mail bcc: '', body: 'Hello, This is an email from jenkins pipeline.', cc: '', from: '', replyTo: '', subject: 'EmailJenkinsPipeline', to: 'sandeepshrinath91@gmail.com'
                      }
                                   }
                }
          }
