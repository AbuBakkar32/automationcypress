pipeline{

    agent any

    parameters{
        string(name: 'SPEC', defaultValue: 'cypress/e2e/**/**', description: 'Enter the script path that you want to execute')
        choice(name: 'BROWSER', choices: ['chrome','edge', 'firefox'], description: 'Select the browser')
    }


    stages{
        stage('Building'){
            steps{
                echo "Building the application"
            }
        }
        stage('Testing'){
            steps{
                echo "Running the test"
                bat "npm install"
                bat "npx cypress run --browser ${BROWSER} --spec ${SPEC}"
            }
        }
         stage('Deploying'){
            steps{
                echo "Deploying the application"
            }
         }
    }

     post{
        always{
            publishHTML([allowMissing: true, alwaysLinkToLastBuild: true, includes: '**/*.png', keepAll: true, reportDir: 'cypress/report', reportFiles: 'index.html', reportName: 'HTML Report', reportTitles: '', useWrapperFileDirectly: true])
        }
     }
}