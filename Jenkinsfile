node {
    def app
    stage('Clone repository') {
        checkout scm
    }
    stage('Build image') {
        when {
            branch 'dev'  
        }
        app = docker.build("isidoraaleksicc/kiii")
    }

    stage('Push image') {
        when {
            branch 'dev'  
        }
        docker.withRegistry('https://registry.hub.docker.com', 'dockerhub2') {
            app.push("${env.BRANCH_NAME}-${env.BUILD_NUMBER}")
            app.push("${env.BRANCH_NAME}-latest")
          
        }
    }
}

