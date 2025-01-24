pipeline {
    environment {
        // Déclaration de la variable d'environnement
        MY_VARIABLE = "Bonjour, ceci est une variable définie dans l'environnement du build !"
    }
    agent any
    stages {

        stage('Afficher la variable') {
            steps {
                script {
                    // Utilisation sécurisée de la variable secrète
                    withCredentials([string(credentialsId: 'MY_BUILD_VARIABLE', variable: 'MY_BUILD_VARIABLE')]) {
                        // Afficher les variables dans la console (Attention : ne pas afficher de secrets en production)
                        echo "La valeur de MY_VARIABLE est : ${env.MY_VARIABLE}"
                        sh 'echo -n "La valeur de MY_BUILD_VARIABLE est : ${MY_BUILD_VARIABLE}" | base64'
                    }
                }
            }
        }
        stage('Checkmarx AST analysis') {
            steps {
                checkmarxASTScanner additionalOptions: '--threshold "sast-high=10; sast-medium=20; sca-high=10" --report-format sarif --output-path "${JENKINS_HOME}/workspace/${JOB_NAME}/" --output-name "help"', baseAuthUrl: '', branchName: 'main', checkmarxInstallation: 'CxOne', credentialsId: '', projectName: 'WebGoat Florian', serverUrl: '', tenantName: '', useOwnAdditionalOptions: true
            }
        }
    }
}
