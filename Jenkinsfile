pipeline {

    agent any

    stages {

        stage('Welcome') {
            steps {
                bat '''
                    echo ==========================================
                    echo Windows Jenkins Multibranch Pipeline
                    echo ==========================================
                '''
            }
        }

        stage('Branch Information') {
            steps {
                bat '''
                    echo.
                    echo Current Branch: %BRANCH_NAME%
                    echo Build Number: %BUILD_NUMBER%
                    echo Job Name: %JOB_NAME%
                    echo Computer Name: %COMPUTERNAME%
                '''
            }
        }

        stage('Build') {
            steps {
                bat '''
                    echo.
                    echo ==========================================
                    echo BUILD STAGE
                    echo ==========================================
                    echo Building application...
                    echo Performing Windows build activities...
                    echo Build completed successfully.
                '''
            }
        }

        stage('Test') {
            steps {
                bat '''
                    echo.
                    echo ==========================================
                    echo TEST STAGE
                    echo ==========================================
                    echo Running tests...
                    echo Checking application configuration...
                    echo Running Windows validation...
                    echo All tests passed successfully.
                '''
            }
        }

        stage('Feature Branch') {
            when {
                expression {
                    return env.BRANCH_NAME.startsWith('feature/')
                }
            }

            steps {
                bat '''
                    echo.
                    echo ==========================================
                    echo FEATURE BRANCH
                    echo ==========================================
                    echo This is a feature branch.
                    echo Feature branch does not deploy.
                    echo Waiting for merge into develop.
                '''
            }
        }

        stage('Development Deployment') {
            when {
                branch 'develop'
            }

            steps {
                bat '''
                    echo.
                    echo ==========================================
                    echo DEVELOPMENT DEPLOYMENT
                    echo ==========================================
                    echo Branch: %BRANCH_NAME%
                    echo Deploying application to Development...
                    echo Restarting Windows application service...
                    echo Development deployment completed.
                '''
            }
        }

        stage('Production Approval') {
            when {
                branch 'main'
            }

            steps {
                input message: 'Deploy to Production?', ok: 'Deploy'
            }
        }

        stage('Production Deployment') {
            when {
                branch 'main'
            }

            steps {
                bat '''
                    echo.
                    echo ==========================================
                    echo PRODUCTION DEPLOYMENT
                    echo ==========================================
                    echo Branch: %BRANCH_NAME%
                    echo Deploying application to Production...
                    echo Restarting Windows application service...
                    echo Verifying application...
                    echo Production deployment completed.
                '''
            }
        }
    }

    post {

        success {
            bat '''
                echo.
                echo ==========================================
                echo PIPELINE COMPLETED SUCCESSFULLY
                echo ==========================================
                echo Branch: %BRANCH_NAME%
                echo Build: %BUILD_NUMBER%
            '''
        }

        failure {
            bat '''
                echo.
                echo ==========================================
                echo PIPELINE FAILED
                echo ==========================================
                echo Branch: %BRANCH_NAME%
                echo Build: %BUILD_NUMBER%
            '''
        }
    }
}
