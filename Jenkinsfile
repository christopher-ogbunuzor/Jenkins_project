// pipeline {
//     def app

//     stage('Clone repository') {
//         /* Let's make sure we have the repository cloned to our workspace */

//         checkout scm
//     }

//     stage('Build image') {
//         /* This builds the actual image; synonymous to
//          * docker build on the command line */

//         app = docker.build("chris-cloudreach/Jenkins_project")
//     }

//     // stage('Test image') {
//     //     /* Ideally, we would run a test framework against our image.
//     //      * For this example, we're using a Volkswagen-type approach ;-) */

//     //     app.inside {
//     //         sh 'echo "Tests passed"'
//     //     }
//     // }

//     stage('Push image') {
//         /* Finally, we'll push the image with two tags:
//          * First, the incremental build number from Jenkins
//          * Second, the 'latest' tag.
//          * Pushing multiple tags is cheap, as all the layers are reused. */
//          docker.withRegistry('https://registry.hub.docker.com', '72721166-66d4-44f1-a089-bd019768e82b'
               
//         app.push("${env.BUILD_NUMBER}")
//         app.push("latest")
        
//     }
// }


pipeline {
    agent any
    options {
        skipStagesAfterUnstable()
    }
    stages {
         stage('Clone repository') { 
            steps { 
                script{
                checkout scm
                }
            }
        }

        stage('Build') { 
            steps { 
                script{
                 app = docker.build("Jenkins_project")
                }
            }
        }
        stage('Test'){
            steps {
                 echo 'Empty'
            }
        }
        stage('Deploy') {
            steps {
                script{
                        docker.withRegistry('https://registry.hub.docker.com', '72721166-66d4-44f1-a089-bd019768e82b') {
                    app.push("${env.BUILD_NUMBER}")
                    app.push("latest")
                    }
                }
            }
        }
    }
}