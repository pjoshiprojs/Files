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
                            def data = readJSON file: 'application.json'
                            for (folder_name in data['folders']) {
                                println "Folder name is : $folder_name"
                                s3Upload(file: folder_name, bucket:'folder-test-jenkins', path: folder_name);
                            }
                        }
                    }
                };
            }
        }
    }
}
