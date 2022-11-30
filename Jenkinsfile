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
                    docker push w1ldweasel/duoflask:latest
                    docker push w1ldweasel/duoflask:$BUILD_NUMBER
                    '''
                }
            }
            stage('Deploy'){
                steps{
                    sh '''
                    kubectl apply -f . # instead of period can have a line for kubectl apply -f [each yaml file]
                    '''
                }
            }
            stage('Cleanup'){
                steps{
                    sh '''
                    docker system prune -a --force
                    '''
                }
            }
        }
}