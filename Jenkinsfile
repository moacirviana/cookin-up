pipeline{
    
    agent any

    stages{
        
        stage("build"){
            steps{
                echo 'building the aplication'
                scripts{
                    def test = 2 + 2 > 3 ? 'cool' : 'not cool'
                    echo test
                }
            }
        }
        
        stage("test"){
            steps{
                echo 'testing the aplication'
            }
        }
        
        stage("deploy"){
            steps{
                echo 'deplying the aplication'
            }
        }
    }
}