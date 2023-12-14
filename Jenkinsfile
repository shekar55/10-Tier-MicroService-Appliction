pipeline {
    agent any
    
    environment{
        
        SCANNER_HOME = tool 'sonar-scanner'
    }

    stages {
        stage('Gitcheckout') {
            steps {
                git branch: 'latest', url: 'https://github.com/shekar55/10-Tier-MicroService-Appliction.git'
            }
        }
        
        stage('sonarqube analysis') {
            steps {
                withSonarQubeEnv('sonar'){
                    sh ''' $SCANNER_HOME/bin/sonar-scanner -Dsonar.projectKey=10-TIER -Dsonar.projectName=10-TIER -Dsonar.java.binaries=.'''
                }   
    
                }
             
            }
            
        stage('adservice') {
            steps {
                script{
                    withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                           dir('/var/lib/jenkins/workspace/10-TIER/src/adservice/') {
                                sh "docker build -t chandu5562/adservice:latest . " 
                                sh "docker push chandu5562/adservice:latest"
                                sh " docker rmi chandu5562/adservice:latest"
                                
                         }
                    }
                }
            }
        }  
        
        stage('cartservice') {
            steps {
                script{
                    withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                           dir('/var/lib/jenkins/workspace/10-TIER/src/cartservice/src/') {
                                sh "docker build -t chandu5562/cartservice:latest . " 
                                sh "docker push chandu5562/cartservice:latest"
                                sh " docker rmi chandu5562/cartservice:latest"
                                
                         }
                    }
                }
            }
        } 
        stage('checkoutservice') {
            steps {
                script{
                    withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                           dir('/var/lib/jenkins/workspace/10-TIER/src/checkoutservice/') {
                                sh "docker build -t chandu5562/checkoutservice:latest . " 
                                sh "docker push chandu5562/checkoutservice:latest"
                                sh " docker rmi chandu5562/checkoutservice:latest"
                                
                         }
                    }
                }
            }
        } 
        
        stage('currencyservice') {
            steps {
                script{
                    withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                           dir('/var/lib/jenkins/workspace/10-TIER/src/currencyservice/') {
                                sh "docker build -t chandu5562/currencyservice:latest . " 
                                sh "docker push chandu5562/currencyservice:latest"
                                sh " docker rmi chandu5562/currencyservice:latest"
                                
                         }
                    }
                }
            }
        } 
        stage('emailservice') {
            steps {
                script{
                    withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                           dir('/var/lib/jenkins/workspace/10-TIER/src/emailservice/') {
                                sh "docker build -t chandu5562/emailservice:latest . " 
                                sh "docker push chandu5562/emailservice:latest"
                                sh " docker rmi chandu5562/emailservice:latest"
                                
                         }
                    }
                }
            }
        } 
        
        stage('frontend') {
            steps {
                script{
                    withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                           dir('/var/lib/jenkins/workspace/10-TIER/src/frontend/') {
                                sh "docker build -t chandu5562/frontend:latest . " 
                                sh "docker push chandu5562/frontend:latest"
                                sh " docker rmi chandu5562/frontend:latest"
                                
                         }
                    }
                }
            }
        } 
        
        stage('loadgenerator') {
            steps {
                script{
                    withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                           dir('/var/lib/jenkins/workspace/10-TIER/src/loadgenerator/') {
                                sh "docker build -t chandu5562/loadgenerator:latest . " 
                                sh "docker push chandu5562/loadgenerator:latest"
                                sh " docker rmi chandu5562/loadgenerator:latest"
                                
                         }
                    }
                }
            }
        } 
        
        stage('paymentservice') {
            steps {
                script{
                    withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                           dir('/var/lib/jenkins/workspace/10-TIER/src/paymentservice/') {
                                sh "docker build -t chandu5562/paymentservice:latest . " 
                                sh "docker push chandu5562/paymentservice:latest"
                                sh " docker rmi chandu5562/paymentservice:latest"
                                
                         }
                    }
                }
            }
        } 
        
        stage('productcatalogservice') {
            steps {
                script{
                    withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                           dir('/var/lib/jenkins/workspace/10-TIER/src/productcatalogservice/') {
                                sh "docker build -t chandu5562/productcatalogservice:latest . " 
                                sh "docker push chandu5562/productcatalogservice:latest"
                                sh " docker rmi chandu5562/productcatalogservice:latest"
                                
                         }
                    }
                }
            }
        }
        
        stage('recommendationservice') {
            steps {
                script{
                    withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                           dir('/var/lib/jenkins/workspace/10-TIER/src/recommendationservice/') {
                                sh "docker build -t chandu5562/recommendationservice:latest . " 
                                sh "docker push chandu5562/recommendationservice:latest"
                                sh " docker rmi chandu5562/recommendationservice:latest"
                                
                         }
                    }
                }
            }
        }
        
        stage('shippingservice') {
            steps {
                script{
                    withDockerRegistry(credentialsId: 'docker-cred', toolName: 'docker') {
                           dir('/var/lib/jenkins/workspace/10-TIER/src/shippingservice/') {
                                sh "docker build -t chandu5562/shippingservice:latest . " 
                                sh "docker push chandu5562/shippingservice:latest"
                                sh " docker rmi chandu5562/shippingservice:latest"
                                
                         }
                    }
                }
            }
        }
        
        stage('k8s-deploy') {
            steps {
                withKubeConfig(caCertificate: '', clusterName: 'my-eks8', contextName: '', credentialsId: 'k8-token2', namespace: 'webapps', restrictKubeConfigAccess: false, serverUrl: 'https://16AE513D3C69C008B427E211867EAB9A.gr7.ap-south-1.eks.amazonaws.com') {
                sh ' kubectl apply -f deployment-service.yml'
                sh ' kubectl get pods'
                sh ' kubectl get svc'
                }
            }
        }
        
       }
    }
 
