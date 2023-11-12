pipeline {
    agent any
    stages {
        stage ('Checkout') {
            steps {
                // add your credentialsId if your repo is private. E.g., credentialsId: 'mingwei1744'
                git branch:'jenkins-lab8', url: 'https://github.com/mingwei1744/ICT3203-SSD-Labs.git'
                }
            }
        stage ('Build') {
            steps {
                sh '/var/jenkins_home/apache-maven-3.6.3/bin/mvn --batch-mode -V -U -e clean verify -Dsurefire.useFile=false -Dmaven.test.failure.ignore'
                }
            }
        stage ('Analysis') {
            steps {
                sh '/var/jenkins_home/apache-maven-3.6.3/bin/mvn --batch-mode -V -U -e checkstyle:checkstyle pmd:pmd pmd:cpd findbugs:findbugs'
                }
            }
    }
    post {
        always {
            junit testResults: '**/target/surefire-reports/TEST-*.xml'
            recordIssues enabledForFailure: true, tools: [mavenConsole(), java(), javaDoc()]
            recordIssues enabledForFailure: true, tool: checkStyle()
            recordIssues enabledForFailure: true, tool: spotBugs(pattern:'**/target/findbugsXml.xml')
            recordIssues enabledForFailure: true, tool: cpd(pattern: '**/target/cpd.xml')
            recordIssues enabledForFailure: true, tool: pmdParser(pattern: '**/target/pmd.xml')
            }
        }
}
