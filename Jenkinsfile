pipeline {
    agent any

    environment {
        REPO=robotshop
        TAG=2.1.0
    }

    stages {

        stage('Checkout') 
        {
            steps 
            {
                git 'https://github.com/YasinMohiddin/three-tier-architecture-demo.git'
            }
        }

        stage('Build Docker Images') 
        {
            parallel 
            {

                stage('User Module')
                {
                    steps 
                    {
                        dir('user') 
                        {
                            sh 'docker build -t user .'
                        }
                    }
                }


                stage('Catalog Module') {
                    steps {
                        dir('catalog') {
                            sh 'docker build -t catalog .'
                        }
                    }
                }

                stage('Cart Module') {
                    steps {
                        dir('cart') {
                            sh 'docker build -t cart .'
                        }
                    }
                }

                stage('Payments Module') {
                    steps {
                        dir('payments') {
                            sh 'docker build -t payment .'
                        }
                    }
                }

                stage('Orders Module') {
                    steps {
                        dir('orders') {
                            sh 'docker build -t $REGISTRY/orders:$IMAGE_TAG .'
                        }
                    }
                }

                stage('Shipping Module') {
                    steps {
                        dir('shipping') {
                            sh 'docker build -t shipping .'
                        }
                    }
                }

                stage('Rating Module') {
                    steps {
                        dir('rating') {
                            sh 'docker build -t rating .'
                        }
                    }
                }

                stage('Dispatch Module') {
                    steps {
                        dir('dispatch') {
                            sh 'docker build -t dispatch .'
                        }
                    }
                }
            }
        }

        stage('Push Docker Images') {
            parallel {

                stage('Push User') {
                    steps {
                        sh 'docker push yasin9/user:myuser'
                    }
                }
                stage('Push Catalog') {
                    steps {
                        sh 'docker push yasin9/catalog:mycatlog'
                    }
                }

                stage('Push Cart') {
                    steps {
                        sh 'docker push yasin9/cart:mycart'
                    }
                }

                stage('Push Payments') {
                    steps {
                        sh 'docker push yasin9/payments:my payments'
                    }
                }

                stage('Push Orders') {
                    steps {
                        sh 'docker push yasin9/orders:myorders'
                    }
                }

                stage('Push Shipping') {
                    steps {
                        sh 'docker push yasin9/shipping:myshipping'
                    }
                }

                stage('Push Rating') {
                    steps {
                        sh 'docker push yasin9/rating:myrating'
                    }
                }

                stage('Push Dispatch') {
                    steps {
                        sh 'docker push yasin9/dispatch:mydispatch'
                    }
                }
            }
        }
    }

    post {
        always {
            sh 'docker system prune -f'
        }
    }
}