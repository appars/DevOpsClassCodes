pipeline {
    agent any

    tools {
        // Install the Maven version configured as "M3" and add it to the path.
        maven "myMaven"
        jdk "myJava"
    }

    stages {
        stage('Compile') {
            steps {
                // Get some code from a GitHub repository
                git 'https://github.com/appars/DevOpsClassCodes.git'

                // Run Maven on a Unix agent.
                sh "mvn compile"
            }
        }
       stage('CodeReview') {
            steps {
                // Run Maven on a Unix agent.
                sh "mvn pmd:pmd"
            }
       }
       stage('UnitTest') {
            steps {
                // Run Maven on a Unix agent.
                sh "mvn test"
            }
            post {
                always {
                    junit 'target/surefire-reports/*.xml'
                }
            }
       }
       stage('Package') {
            steps {
                // Run Maven on a Unix agent.
                sh "mvn package"
            }
       }
    }
}
