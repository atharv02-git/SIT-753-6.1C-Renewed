pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo 'Build task is a stage where code is compiled into an executable format.'
                echo 'Maven Tool:'
                echo 'Automation tool for Java projects that manages dependencies, compiles code, runs tests.'
            }
        }
        stage('Test') {
            steps {
                echo 'Unit Testing'
                echo 'Ensures that individual components work correctly.'
                echo 'Mocha/Chai is a popular dependency used for unit testing in JavaScript/Node.js projects.'
                echo 'Integration Testing:'
                echo 'Different aspects of code work together as expected.'
                echo 'Postman:'
                echo 'Used for API testing, making it useful for integration tests involving RESTful services.'
            }
            post {
                always {
                    mailext(
                        to: 'atharvsbhandare@gmail.com',
                        subject: "Jenkins Build: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                        body: """<p>Stage 'Unit and Integration Test' completed with status: ${currentBuild.currentResult ?: 'SUCCESS'}</p>
                                 <p>Check console output at <a href="${env.BUILD_URL}">${env.BUILD_URL}</a> to view the results.</p>""",
                        attachLog: true
                    )
                }
            }
        }
        stage('Code Analysis') {
            steps {
                echo 'Code Analysis'
                echo 'It is basically a quality assurance stage that improves code quality and reduces risks.'
                echo 'ESLint:'
                echo 'A tool for analyzing JavaScript code for style issues, best practices, and potential bugs.'
            }
        }
        stage('Security Scan') {
            steps {
                echo 'Security scan helps identify vulnerabilities, weaknesses, and other security risks in codebases.'
                echo 'Veracode:'
                echo 'A scan which analyzes source code for security vulnerabilities without executing the code.'
                echo 'Identifies common security flaws like SQL injection, XSS, and hardcoded secrets.'
            }
            post {
                always {
                    emailext(
                        to: 'atharvsbhandare@gmail.com',
                        subject: "Jenkins Build: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                        body: """<p>Stage 'Security Scan' completed with status: ${currentBuild.currentResult ?: 'SUCCESS'}</p>
                                 <p>Check console output at <a href="${env.BUILD_URL}">${env.BUILD_URL}</a> to view the results.</p>""",
                        attachLog: true
                    )
                }
            }
        }
        stage('Deploy to staging') {
            steps {
                echo 'Refers to the process of deploying an application to a production or test environment.'
                echo 'AWS EC2 deploy:'
                echo 'A deployment service provided by AWS that automates deploying applications to EC2 instances.'
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                echo 'Integration testing is a crucial step in the software development lifecycle.'
                echo 'Aims to verify that different components or systems work together as expected.'
                echo 'Selenium: For automating browser-based tests, useful for testing web applications.'
            }
        }
        stage('Deploy to production') {
            steps {
                echo 'Deploy the application to the production server from the staging server.'
                echo 'The same AWS EC2 instance can be used to deploy to the production server.'
            }
        }
    }
}
