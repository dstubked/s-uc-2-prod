node {
    def app

    stage('Clone repository') {
        /* Clone repository to our workspace */

        checkout scm
    }

    stage('Pull Dev Image') {
        /* This builds the actual image */

        origapp = docker.pull("dstubked-docker.jfrog.io/orders-nginx-dev:good")
    }
    
    stage ('Aqua Scan Dev App') {
        aqua customFlags: '--layer-vulnerabilities', hideBase: false, hostedImage: '', localImage: 'dstubked-docker.jfrog.io/orders-nginx-dev:good', locationType: 'local', notCompliesCmd: '', onDisallowed: 'fail', policies: '', register: true, registry: 'JFrog', showNegligible: false
    }
    
    /*stage('Push image') {
        docker.withRegistry('https://dstubked-docker.jfrog.io', 'jfrog') {
            app.push()
        }
    }*/
}
