node {

   def registryProjet='formation/'
   def IMAGE="melibob/app:3.8"

    stage('Clone') {
          checkout scm
    }

    def img = stage('Build') {
          docker.build("$IMAGE",  '.')
    }

    stage('Run') {
          img.withRun("--name run-$BUILD_ID -p 8000:80") { c ->
       
          }
    }

    stage('Push') {
       docker.withRegistry('https://registry.hub.docker.com/' , 'docker_id') {
              img.push 'latest'
              img.push()
          }
    }

}

