pipeline{
        agent any
        stages{
            stage('Build'){
                steps{
                    sh '''
                    docker build -t w1ldweasel/duoflask:latest -t w1ldweasel/duoflask:$BUILD_NUMBER .
                    '''
                }
            }
            stage('Push'){
                steps{
                    sh '''
                    docker push w1ldweasel/duoflask:latest w1ldweasel/duoflask:$BUILD_NUMBER .
                    '''
                }
            }
            stage('Deploy'){
                steps{
                    sh '''
                    kubectl apply -f .
                    '''
                }
            }
        }
}