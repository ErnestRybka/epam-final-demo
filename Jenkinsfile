node {
    def app

    stage('Clone repository locally') {
        /* Let's make sure we have the repository cloned to our workspace */

        checkout scm
    }
    stage('Build image') {
        /* This builds the actual image; synonymous to
         * docker build on the command line */

        app = docker.build("rybkaer/extension_lab_backend")
        app.push()
    }
}

node('aws_1'){

    stage('pull image'){
        sh "docker pull rybkaer/extension_lab_backend"
    }
    
    stage('stop/delite all containers'){
       sh "docker stop \$(docker ps -a -q) || true"
       sh "docker rm \$(docker ps -a -q) || true"
    }


    stage('run image') {
        sh "docker-compouse up"
    }
    
}

node('aws_2'){

    stage('pull image'){
        sh "docker pull rybkaer/extension_lab_backend"
    }
    
    stage('stop/delite all containers'){
       sh "docker stop \$(docker ps -a -q) || true"
       sh "docker rm \$(docker ps -a -q) || true"
    }


    stage('run image') {
        sh "docker-compouse up"
    }
    
}