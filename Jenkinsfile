pipeline{
        agent any
        stages{
            stage('Build'){
                steps{
                    sh "rmdir -rf ~/kubebuilds"
                    sh "mkdir ~/kubebuilds"
                    sh "cd ~/kubebuilds"
                    sh "git clone git@github.com:w1ldweasel/duotasks.git"
                    sh "cd duotasks"
                }
            }
            stage('Deploy'){
                steps{
                    sh "kubectl apply -f flaskapp.yaml"
                    sh "kubectl apply -f webserver.yaml"
                }
            }
        }
}