pipeline{
    agent any
    stages{
        stage("Build"){
            agent {
                docker {
                    image 'node:18-alpine'
                    reuseNode true
                }
            }
            environment {
                    NPM_CONFIG_CACHE = "${WORKSPACE}/.npm"   // cache npm ไว้ใน workspace
            }
            steps{
                sh '''
                    ls -la
                    npm --version
                    node --version
                    rm -rf node_modules package-lock.json
                    npm cache clean --force
                    npm install

                    npm run build
                    ls -la
                '''
            }
           
        }
        stage('Test'){
            agent {
                docker {
                    image 'node:18-alpine'
                    reuseNode true
                }
            }
            steps{
                sh '''
                test -f build/index.html
                npm test
                '''
            }
        }
    }
 
}