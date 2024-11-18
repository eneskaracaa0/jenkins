pipeline {
    agent {
        docker {
            image 'node:18-alpine' // Node.js 18 Alpine imajı
            args '-u root'        // Root kullanıcısı ile çalıştırma
        }
    }

    environment {
        // Ortak kullanılacak bir ortam değişkeni tanımlayabilirsiniz.
        NODE_ENV = 'production'
    }

    stages {
        stage('Install Dependencies') {
            steps {
                script {
                    echo 'Installing dependencies...'
                }
                sh '''
                    # Node.js ve npm sürümünü kontrol edelim
                    node --version
                    npm --version

                    # Bağımlılıkları yükleyelim
                    npm ci
                '''
            }
        }

        stage('Run Tests') {
            steps {
                script {
                    echo 'Running tests...'
                }
                sh '''
                    # Testleri çalıştır
                    npm test
                '''
            }
        }

        stage('Build Project') {
            steps {
                script {
                    echo 'Building project...'
                }
                sh '''
                    # Üretim yapısını oluştur
                    npm run build

                    # Build dizinini kontrol et
                    ls -la build
                '''
            }
        }
    }

    post {
        always {
            echo 'Pipeline finished!'
        }
        success {
            echo 'Build succeeded!'
        }
        failure {
            echo 'Build failed.'
        }
    }
}
