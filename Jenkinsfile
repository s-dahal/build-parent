@Library("titan-library") _

pipeline {
    agent any

    environment {

        SONAR_AUTH_TOKEN    = credentials('sonarqube_pac_token')
        SONARQUBE_URL       = "${GLOBAL_SONARQUBE_URL}"
        SONAR_HOST_URL      = "${GLOBAL_SONARQUBE_URL}"

        BRANCH_NAME         = "${GIT_BRANCH.split("/").size() > 1 ? GIT_BRANCH.split("/")[1] : GIT_BRANCH}"

    }

    options {

        // Set this to true if you want to clean workspace during the prep stage
        skipDefaultCheckout(false)

        // Console debug options
        timestamps()
        ansiColor('xterm')
    }

    stages {

        stage('stage main'){
            when {
                beforeAgent true
                anyOf{
                    branch "main"
                    branch "master"
                }
            }
            steps{
                sh '''
                    echo executing main branch
                '''
            }
        }

        stage('stage feature branch'){
            when {
                beforeAgent true
                not{
                    anyOf{
                        branch "main"
                        branch "master"
                    }
                }
            }
            steps{
                sh '''
                    echo "executing feature branch"
                '''
            }
        }

        stage('Maven Build') {
            agent {
                docker {
                    image "maven:3.8.7-eclipse-temurin-19-focal"
                    args '-u root:root'
                }
            }

            steps {
                sh '''
                    echo "executing feature branch"
                '''
            }
        }

        stage("Publish to Nexus Repository Manager") {

            when {
                beforeAgent true
                anyOf{
                    branch "main"
                    branch "master"
                }
            }

            agent {
                docker {
                    image "maven:3.8.7-eclipse-temurin-19-focal"
                    args '-u root:root'
                }
            }

            steps {
                sh '''
                    echo "executing feature branch"
                '''
            }
        }

        stage("Deploy skipped") {

            when {
                expression { return changeRequest() }
            }

            steps {
                echo 'Skipped Deploy as this is PullRequest'
            }
        }
    }


    post {
        always {
            // Clean the workspace after build
            cleanWs(cleanWhenNotBuilt: false,
                deleteDirs: true,
                disableDeferredWipeout: true,
                notFailBuild: true,
                patterns: [
                [pattern: '.gitignore', type: 'INCLUDE']
            ])
        }
    }
}
