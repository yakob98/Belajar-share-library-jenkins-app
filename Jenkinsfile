// pipeline{
//     agent any

//     stages{
//         stage("Hello"){
//             steps{
//                 echo "Hello World"
//             }
//         }
//     }
// }

pipeline{
    agent{
        node{
            label "java && jenkins"
        }
    }

    stages{
        stage("Hello"){
            steps{
                echo "Hello World"
            }
        }
    }
}