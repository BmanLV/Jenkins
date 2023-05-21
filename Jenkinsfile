pipeline {
    agent any
    
    stages {
        stage("install-pip-deps") {
            steps {
               echo 'Installing all required dependencies..'
                dir('my-repo') {
                    git 'https://github.com/mtararujs/python-greetings'
                    
                    sh 'ls'
                    
                    sh 'pip3 install -r requirements.txt'
                }
            }
        }
        
        stage("deploy-to-dev") {
            steps {
              echo 'Deploying to dev environment..'
                dir('my-repo') {
                    git 'https://github.com/mtararujs/python-greetings'
                    
                    sh 'pm2 delete greetings-app-dev & set "errorlevel=0"'
                    
                    sh 'pm2 start app.py --name greetings-app-dev -- --port 7001'
                }
            }
        }
        
        stage("tests-on-dev") {
            steps {
                echo 'Running tests on dev environment..'
                dir('my-repo') {
                    git 'https://github.com/mtararujs/course-js-api-framework'
                    
                    sh 'npm install'
                    
                    sh 'npm run greetings greetings_dev'
                }
            }
        }
        
        stage("deploy-to-staging") {
            steps {
                echo 'Deploying to staging environment..'
                dir('my-repo') {
                    git 'https://github.com/mtararujs/python-greetings'
                    
                    sh 'pm2 delete greetings-app-staging & set "errorlevel=0"'
                    
                    sh 'pm2 start app.py --name greetings-app-staging -- --port 7002'
                }
            }
        }
        
        stage("tests-on-staging") {
            steps {
                echo 'Running tests on staging environment..'
                dir('my-repo') {
                    git 'https://github.com/mtararujs/course-js-api-framework'
                    
                    sh 'npm install'
                    
                    sh 'npm run greetings greetings_staging'
                }
            }
        }
        
        stage("deploy-to-preprod") {
            steps {
                echo 'Deploying to preprod environment..'
                dir('my-repo') {
                    git 'https://github.com/mtararujs/python-greetings'
                    
                    sh 'pm2 delete greetings-app-preprod || true'
                    
                    sh 'pm2 start app.py --name greetings-app-preprod -- --port 7003'
                }
            }
        }
        
        stage("tests-on-preprod") {
            steps {
                echo 'Running tests on preprod environment..'
                dir('my-repo') {
                    git 'https://github.com/mtararujs/course-js-api-framework'
                    
                    sh 'npm install'
                    
                    sh 'npm run greetings greetings_preprod'
                }
            }
        }
        
        stage("deploy-to-prod") {
            steps {
                echo 'Deploying to prod environment..'
                dir('my-repo') {
                    git 'https://github.com/mtararujs/python-greetings'
                    
                    sh 'pm2 delete greetings-app-prod || true'
                    
                    sh 'pm2 start app.py --name greetings-app-prod -- --port 7004'
                }
            }
        }
        
        stage("tests-on-prod") {
            steps {
                echo 'Running tests on prod environment..'
                dir('my-repo') {
                    git 'https://github.com/mtararujs/course-js-api-framework'
                    
                    sh 'npm install'
                    
                    sh 'npm run greetings greetings_prod'
                }
            }
        }
    }
}
