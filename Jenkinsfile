pipeline {
    agent any

    environment {
        DOCKERHUB_CREDENTIALS = credentials('dockerhub')
    }
    stages {
        stage('Environment preparation') {
            steps {

                echo "-=- This from branch Develop -=-"
                echo "-=- First push from develop -=-"

                // sh "cp .env .env.bak"

                // withCredentials([string(credentialsId: 'OPENAI_API_KEY', variable: 'OPENAI_API_KEY')]) {
                //     sh "sed -i \"s/OPENAI_API_KEY=OPENAI_API_KEY/OPENAI_API_KEY=$OPENAI_API_KEY/g\" .env"
                // }

                // withCredentials([string(credentialsId: 'POSTGRES_USER', variable: 'POSTGRES_USER')]) {
                //     sh "sed -i \"s/POSTGRES_USER=POSTGRES_USER/POSTGRES_USER=$POSTGRES_USER/g\" .env"
                // }

                // withCredentials([string(credentialsId: 'POSTGRES_DATABASE', variable: 'POSTGRES_DATABASE')]) {
                //     sh "sed -i \"s/POSTGRES_DATABASE=POSTGRES_DATABASE/POSTGRES_DATABASE=$POSTGRES_DATABASE/g\" .env"
                // }

                // withCredentials([string(credentialsId: 'POSTGRES_HOST', variable: 'POSTGRES_HOST')]) {
                //     sh "sed -i \"s/POSTGRES_HOST=POSTGRES_HOST/POSTGRES_HOST=$POSTGRES_HOST/g\" .env"
                // }

                // withCredentials([string(credentialsId: 'KEYCLOAK_REALM', variable: 'KEYCLOAK_REALM')]) {
                //     sh "sed -i \"s/KEYCLOAK_REALM=KEYCLOAK_REALM/KEYCLOAK_REALM=$KEYCLOAK_REALM/g\" .env"
                // }

                // withCredentials([string(credentialsId: 'KEYCLOAK_SERVER_URL', variable: 'KEYCLOAK_SERVER_URL')]) {
                //     sh "sed -i \"s@KEYCLOAK_SERVER_URL=KEYCLOAK_SERVER_URL@KEYCLOAK_SERVER_URL=$KEYCLOAK_SERVER_URL@g\" .env"
                // }

                // withCredentials([string(credentialsId: 'KEYCLOAK_CLIENT_ID', variable: 'KEYCLOAK_CLIENT_ID')]) {
                //     sh "sed -i \"s@KEYCLOAK_CLIENT_ID=KEYCLOAK_CLIENT_ID@KEYCLOAK_CLIENT_ID=$KEYCLOAK_CLIENT_ID@g\" .env"
                // }

                // withCredentials([string(credentialsId: 'KEYCLOAK_CLIENT_SECRET', variable: 'KEYCLOAK_CLIENT_SECRET')]) {
                //     sh "sed -i \"s@KEYCLOAK_CLIENT_SECRET=KEYCLOAK_CLIENT_SECRET@KEYCLOAK_CLIENT_SECRET=$KEYCLOAK_CLIENT_SECRET@g\" .env"
                // }

                // withCredentials([string(credentialsId: 'MIMIC_SERVICE_HOST', variable: 'MIMIC_SERVICE_HOST')]) {
                //     sh "sed -i \"s@MIMIC_SERVICE_HOST=MIMIC_SERVICE_HOST@MIMIC_SERVICE_HOST=$MIMIC_SERVICE_HOST@g\" .env"
                // }

                // withCredentials([string(credentialsId: 'CONTENT_SERVICE', variable: 'CONTENT_SERVICE')]) {
                //     sh "sed -i \"s@CONTENT_SERVICE=CONTENT_SERVICE@CONTENT_SERVICE=$CONTENT_SERVICE@g\" .env"
                // }

                // withCredentials([string(credentialsId: 'IDENTIFY_SERICE', variable: 'IDENTIFY_SERICE')]) {
                //     sh "sed -i \"s@IDENTIFY_SERICE=IDENTIFY_SERICE@IDENTIFY_SERICE=$IDENTIFY_SERICE@g\" .env"
                // }

                // withCredentials([string(credentialsId: 'POSTGRES_PASSWORD', variable: 'POSTGRES_PASSWORD')]) {
                //     sh "sed -i \"s@POSTGRES_PASSWORD=POSTGRES_PASSWORD@POSTGRES_PASSWORD=$POSTGRES_PASSWORD@g\" .env"
                // }
                
                sh "cat .env"
            }
        }

        // stage('SonarQube Analysis') {
        //     steps {

        //         echo "-=- SonarQube Analysis -=-"

        //         withCredentials([
        //             string(credentialsId: 'sonarqube_host', variable: 'sonarqube_host'),
        //             string(credentialsId: 'dev_ai_project_key', variable: 'dev_ai_project_key'),
        //             string(credentialsId: 'dev_ai_project_token', variable: 'dev_ai_project_token'),
        //             ]) {
        //                    sh '''
        //                         sonar-scanner \
        //                         -Dsonar.projectKey=dev_ai_svc \
        //                         -Dsonar.sources=. \
        //                         -Dsonar.host.url=http://11.11.7.200:9001 \
        //                         -Dsonar.token=sqp_c4c67448b1e1e5cdc9ec547e28bcd6b31e568b0e
        //                    ''' 
        //         }

        //     }
        // }


        stage('Tests') {
            steps {
                script {
                    def branchName = scm.branches[0].name

                    if (branchName == '*/develop') {
                        echo "From branch Develop"

                    }

                    if (branchName == '*/main') {
                        echo "From branch Main"
                    }
                }
            }
        }

        // stage('Build Docker image') {
        //     steps {
        //         echo "-=- build Docker image -=-"
        //         sh "docker build -t rlgthi/test:latest ."
        //     }
        // }


        // stage('Push Docker image') {
        //     steps {
        //         echo "-=- push Docker image -=-"

        //         sh "echo '$DOCKERHUB_CREDENTIALS_PSW' | docker login -u '$DOCKERHUB_CREDENTIALS_USR' --password-stdin"
        //         sh "docker push rlgthi/test:latest"
        //     }
        // }

        // stage('Run Container') {
        //     steps {
        //         echo "-=- run container -=-"

        //         script {
        //             def old_container = sh(returnStdout: true, script: 'docker ps -aqf "name=test"').trim()
        //             if (old_container) {

        //                 // Stop and remove old container
        //                 sh "docker stop ${old_container}"
        //                 sh "docker rm ${old_container}"

        //             }
        //         }

        //         sh "docker run -d -p 5555:5000 --name test rlgthi/test:latest"
        //     }
        // }

        stage('Deploy') {
            steps {
                // script {
                //     if (env.BRANCH_NAME == 'develop') {
                //         // Deploy to dev server
                //         sh 'ansible-playbook -i ansible/dev-server ansible/deploy-dev.yml'
                //     } else if (env.BRANCH_NAME == 'main') {
                //         // Deploy to prod server
                //         sh 'ansible-playbook -i ansible/prod-server ansible/deploy-prod.yml'
                //     } else {
                //         error "Unsupported branch for deployment: ${env.BRANCH_NAME}"
                //     }
                // }
                sh 'pwd'

                sh 'printenv'

            }
        }
    }

    post {
        always {
            echo "-=- remove deployment -=-"
            sh 'echo End'
        }
    }
}
