pipeline {
    environment {
        // Déclaration de la variable d'environnement
        MY_VARIABLE = "Bonjour, ceci est une variable définie dans l'environnement du build !"
    }

    agent { docker { image 'maven:3.9.9-eclipse-temurin-21-alpine' } }
    stages {
        stage('build') {
            steps {
                sh 'mvn --version'
            }
        }
        stage('Afficher la variable') {
            steps {
                script {
                    // Afficher la variable dans la console
                    echo "La valeur de MY_VARIABLE est : ${env.MY_VARIABLE}"
                    echo "La valeur de MY_BUILD_VARIABLE est : ${MY_BUILD_VARIABLE}"
                }
            }
        }
    }
}
