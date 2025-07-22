node {
    
    def registryProjet='rania243/'
    def IMAGE="${registryProjet}cicd:version-${env.BUILD_ID}"
    
    stage('Clone') {
        checkout scm
    }
    
    def img = stage('Build') {
        docker.build("$IMAGE", '.')
    }
    
    stage('Run') {
        img.withRun("--name run-$BUILD_ID -p 8000:80") { c ->
            
        }
    }
    
    stage('Push') {
        docker.withRegistry('https://registry.hub.docker.com', 'docker-id') {
            img.push 'latest'
            img.push()
        }
    }
}
