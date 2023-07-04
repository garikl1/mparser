def imageName = 'garikl1/mparser'
node('workers'){
        stage('Checkout'){
          git branch: 'develop',
            credentialsId: 'github-ssh',
            url: 'git@github.com:garikl1/mparser.git'
        }

        def imageTest = docker.build("${imageName}-test", "-f Dockerfile.test .")

        stage('Unit Tests') {
          //sh "docker run -i ${imageName}-test go test"
          imageTest.inside('-u root:root') {
            sh 'go test'
          }
        }

        stage('Security Tests') {
         // imageTest.inside('-u root:root') {
         //   sh 'nancy sleuth -p Gopkg.lock'
         // }
         sh 'docker run -i garikl1/mparser-test nancy sleuth -p Gopkg.lock'
        }

}