def imageName = 'garikl1/mparser'
node('workers'){
        stage('Checkout'){
          git branch: 'develop',
            credentialsId: 'github-ssh',
            url: 'git@github.com:garikl1/mparser.git'
        }

        def imageTest = docker.build("${imageName}-test", "-f Dockerfile.test .")
        stage('Unit Tests') {
          imageTest.insde( sh 'go test' )  
        }

}