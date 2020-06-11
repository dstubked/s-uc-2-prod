node {
    def app

    stage('Clone repository') {
        /* Clone repository to our workspace */

        checkout scm
    }
    
   stage ('Aqua Scan Dev Namespace') {
        aqua customFlags: '--layer-vulnerabilities', hideBase: false, hostedImage: 'dstubked-docker.jfrog.io/orders-nginx-dev:good', localImage: '', locationType: 'hosted', notCompliesCmd: '', onDisallowed: 'fail', policies: '', register: false, registry: 'JFrog', showNegligible: false
    }    
   /*stage('Pull image') {
        docker.withRegistry('https://dstubked-docker.jfrog.io', 'jfrog') {
            sh "docker pull dstubked-docker.jfrog.io/orders-nginx-dev:good"
        }
    }*/
    
    /*stage('Pull Dev Image') {
        /* This builds the actual image /*
        sh "docker pull dstubked-docker.jfrog.io/orders-nginx-dev:good"
        origapp = docker.pull("dstubked-docker.jfrog.io/orders-nginx-dev:good")
    }*/
    
    /*stage('Push image') {
        docker.withRegistry('https://dstubked-docker.jfrog.io', 'jfrog') {
            app.push()
        }
    }*/
}
