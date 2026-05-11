pipeline('built-in')
{
    agent any

    stages
    {
        stage('download')
        {
            steps
            {
                echo 'Downloading...'
                git 'https://github.com/yasinmohiddin/three-tier-architecture-demo.git'
            }
        }
        stage('Build')
        {
            steps
            {
                echo 'Building...'
                'mvn clean package'
                'npm install'
            }
        }
        stage('Test')
        {
            steps
            {
                echo 'Testing...'
            }
        }
        stage('Deploy')
        {
            steps
            {
                echo 'Deploying...'
            }
        }
    }
}