pipeline{
    agent none
    
    stages{
        stage('build'){
            agent{
                label 'buildnode'
            }
            steps{
                deleteDir()
                
                sh'''
                git clone https://github.com/badusha07/task.git
                ls -la
                '''
                
                stash name:'webpage',includes:'task/**'
            }
        }
        
        stage('deploy'){
            agent{
                label'deploynode'
            }
            steps{
                deleteDir()
                
                unstash'webpage'
                
                sh'''
                rm -rf /var/www/html/*
                cp -r task/* /var/www/html/
                ls -la
                '''
            }
        }
    }
}
