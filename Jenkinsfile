def imageName = 'garikl1/mparser'
node('workers'){
        stage('Checkout'){
          git branch: 'develop',
            credentialsId: 'github-ssh',
            url: 'git@github.com:garikl1/mparser.git'
        }
        stage('Unit Tests') {
          def imageTest = docker.build("${imageName}-test", "-f Dockerfile.test .")
          imageTest.inside{ sh "${GOPATH}/bin/golint" }
        }

}