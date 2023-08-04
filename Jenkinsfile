// Pipeline untuk menjalankan task di agent mana pun yang sedang kosong
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

// Menargetkan agent dengan menggunakan label untuk menjalankan task
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

    post{
        always{
            echo "Kita akan selalu bertemu"
        }
        success{
            echo "Yes Berhasil Run"
        }
        failure{
            echo "Yahhh Gagal :("
        }
        cleanup{
            echo "Apapun yang terjadi tetap harus di bersihkan"
        }
    }
}