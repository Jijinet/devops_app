node {   
    stage('Clone repository') {
        git credentialsId: 'git', url: 'https://github.com/amachlou/devops_app'
    }
    
    stage('Build image') {
       dockerImage = docker.build("jijinet/tp4_devops:"+ "$BUILD_NUMBER")
    }
    
    stage('Push image') {
        withDockerRegistry([ credentialsId: "DOCKER_HUB", url: "" ]) {
        dockerImage.push()
        }
    }  
    
    stage('Deploy image') {
        bat "docker run -d jijinet/tp4_devops:$BUILD_NUMBER"
    }
    
}