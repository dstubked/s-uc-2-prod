node {
    def app

    stage('Clone repository') {
        /* Clone repository to our workspace */

        checkout scm
    }
    
   stage ('Aqua Scan Dev Namespace') {
        aqua customFlags: '--layer-vulnerabilities', hideBase: false, hostedImage: 'orders-nginx-dev:good', localImage: '', locationType: 'hosted', notCompliesCmd: '', onDisallowed: 'fail', policies: '', register: false, registry: 'JFrog', showNegligible: true
    }    
   stage('Package Dev Image') {
        docker.withRegistry('https://dstubked-docker.jfrog.io', 'jfrog') {
            sh "docker pull dstubked-docker.jfrog.io/orders-nginx-dev:good"
            sh "docker tag dstubked-docker.jfrog.io/orders-nginx-dev:good dstubked-docker.jfrog.io/orders-nginx-prod:good"
        }
    }
    stage ('Aqua Scan Prod Namespace') {
        aqua customFlags: '--layer-vulnerabilities', hideBase: false, hostedImage: '', localImage: 'dstubked-docker.jfrog.io/orders-nginx-prod:good', locationType: 'local', notCompliesCmd: '', onDisallowed: 'fail', policies: '', register: true, registry: 'JFrog', showNegligible: false
    } 
    stage('Push into Prod Namespace') {
        docker.withRegistry('https://dstubked-docker.jfrog.io', 'jfrog') {
            sh "docker push dstubked-docker.jfrog.io/orders-nginx-prod:good"
        }
    }
    
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
