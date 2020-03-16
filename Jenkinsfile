pipeline {
    agent any
    stages {
        stage('build') {
            steps {
                echo ghprbSourceBranch
                echo ghprbActualCommit
                echo ghprbActualCommitAuthor
                echo ghprbActualCommitAuthorEmail
                echo ghprbPullDescription
                echo ghprbPullId
                echo ghprbPullLink
                echo ghprbPullTitle
                echo ghprbTargetBranch
                echo ghprbCommentBody
                echo sha1
            }
        }
        stage('getCode'){
            steps{
                git branch: ghprbSourceBranch,
                    credentialsId: 'github-ssh',
                    url: 'git@github.com:BlueShells/testpipelinejenkins.git'
                sh 'pwd'
                sh 'ls -al'
            }
        }
        stage('test'){
            steps{
                sh '/usr/bin/pylint 1.py' 
            }
        }
        stage('read'){
             steps {
               script {
                   def data = readFile(file: 'pylint_result.txt')
                   println(data)
               }
             }
        }
    }
}
