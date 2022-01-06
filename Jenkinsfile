pipeline {
    agent {
        docker { image 'ubuntu:latest' }
    }
    stages {
        stage('Test') {
            steps {
                dir('Files/src/main/resources/'){
                    withAWS(region:'us-east-1',credentials:'aws') {
                        script {
                            def props = readProperties file: 'application.properties'
                            def folder_name= props['folder.name']
                            println(folder_name)
                            s3Upload(file: folder_name, bucket:'folder-test-jenkins', path: folder_name);
                        }
                    }
                };
            }
        }
    }
}
