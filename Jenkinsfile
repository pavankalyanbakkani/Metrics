pipeline {
    agent {
        node {
            label 'built-in' // Use Jenkins' built-in node
        }
    }
    
    stages {
        stage('Build') {
            steps {
                echo 'Hello, World! Im here again'
                echo 'Hell yeah !..........................'
            }
        }
        stage('Show Desc') {
            steps {
                echo 'Trying Hard to fetch metrics'
                echo 'Plz come asap..........................'
            }
        }
    }
    
    post {
        success {
            script {
                def commitSHA = 'YOUR_SHA'  // You'd typically fetch this dynamically
                def response = httpRequest url: 'https://app.sleuth.io/api/1/deployments/testtoken/metrics-3/register_deploy',
                                           httpMode: 'POST',
                                           contentType: 'APPLICATION_JSON',
                                           headers: [
                                                [name: 'Authorization', value: 'Bearer YOUR_ACTUAL_ORG_REGISTER_DEPLOY_ACCESS_TOKEN']
                                           ],
                                           validResponseCodes: '100:599',
                                           requestBody: "{\"environment\": \"production\", \"sha\": \"${commitSHA}\"}"

                echo "Response from Sleuth: ${response}"
            }
        }
    }
}
