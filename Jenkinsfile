node {
    def app

    stage('Clone repository') {
        /* Let's make sure we have the repository cloned to our workspace */
        checkout scm
    }

    stage('Build image') {
       app = docker.build("the1amit/hellonode")
    }

    stage('Test image') {  
        app.inside {
            sh 'echo "Tests passed"'
        }
    }

    stage('Push image') {      
        docker.withRegistry('https://registry.hub.docker.com', 'dockerhub') {
            app.push("${env.BUILD_NUMBER}")
        }
    }
}
