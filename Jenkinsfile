pipeline {
    agent {
        // Node.js image kullanarak Jenkins container'ını çalıştırıyoruz
        docker {
            image 'node:14' // Örneğin, Node.js 14 sürümünü kullanıyoruz
            args '-u root'  // Gerekirse root izinleriyle çalıştırabiliriz
        }
    }
    environment {
        // Çevresel değişkenleri tanımlayabilirsiniz
        NODE_ENV = 'development'
    }
    stages {
        stage('Install Dependencies') {
            steps {
                // Bağımlılıkları yüklüyoruz
                sh 'npm install'
            }
        }
        stage('Test') {
            steps {
                // Testleri çalıştırıyoruz
                sh 'npm test'
            }
        }
        stage('Build') {
            steps {
                // Projeyi build ediyoruz (varsa)
                sh 'npm run build'
            }
        }
    }
    post {
        success {
            echo 'Pipeline başarıyla tamamlandı.'
        }
        failure {
            echo 'Pipeline başarısız oldu.'
        }
    }
}
