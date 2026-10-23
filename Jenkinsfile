pipeline {
    agent {
        docker {
            image 'alpine/jmeter:5.6.3'
            args '--entrypoint=""'
        }
    }
    stages {
        stage('Performance Tests') {
            steps {
                sh 'jmeter -n -t Peclinic-rest.jmx -l petclinic-results.jtl'
                  sh 'pwd'
                  sh 'ls -la ${WORKSPACE}'
            }
        }
        stage('Publish Results') {
            steps {


                perfReport sourceDataFiles: 'petclinic-results.jtl'
            }
        }
    }
}

//PARA HABILITAR JAVASCRIPT EN JENKIS DE MANERA ETEMPORAL
//EJECUTAR EN SU CONSOLA DE SCRIPTS
//System.setProperty("hudson.model.DirectoryBrowserSupport.CSP","")