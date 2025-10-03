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
            steps{
                sh '''
                    ls -la
                    npm --version
                    node --version
                    rm -rf node_modules package-lock.json
                    npm cache clean --force
                    npm install

                    npm run build
                    ls -laA
                '''
            }
           
        }
    }
 
}