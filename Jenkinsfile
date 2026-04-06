pipeline {
    // 'agent any' le dice a Jenkins que ejecute esto en cualquier nodo disponible
    agent any

    stages {
        stage('Preparación (Checkout)') {
            steps {
                // Descarga el código de tu rama actual de GitHub
                checkout scm
                echo '✅ Código de WordPress descargado correctamente del repositorio.'
            }
        }

        stage('Pruebas Básicas') {
            steps {
                echo '🔍 Verificando el código de WordPress...'
                // Aquí podrías validar la sintaxis de tus plugins o temas.
                // Como ejemplo, simplemente imprimimos la versión de PHP si está disponible.
                sh 'php -v || echo "PHP no está instalado en el agente local, omitiendo prueba."'
            }
        }

        stage('Construcción / Preparar Docker') {
            steps {
                echo '🐳 Preparando imágenes o contenedores...'
                // Aquí podrías reconstruir tu imagen de WordPress si tuvieras un Dockerfile específico para él
                // sh 'docker-compose build wordpress'
            }
        }

        stage('Despliegue') {
            steps {
                echo '🚀 Aplicando cambios en el entorno...'
                // Comandos típicos para reiniciar o actualizar los servicios sin tirar la base de datos
                // sh 'docker-compose up -d --no-deps --build wordpress'
                echo 'Despliegue simulado finalizado.'
            }
        }
    }

    // El bloque 'post' se ejecuta siempre al final, sin importar si falló o fue exitoso
    post {
        success {
            echo '🎉 ¡El Pipeline se ejecutó correctamente! El nuevo código de WordPress está listo.'
        }
        failure {
            echo '❌ Algo falló en el proceso. Revisa los logs de arriba.'
        }
        always {
            echo '🧹 Limpieza final ejecutada.'
        }
    }
}