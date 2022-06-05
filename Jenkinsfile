pipeline  {
    agent any
    // agent{
    //     node {
    //         label 'OD'
    //     }
    // } 
    
    // triggers {
    //     // cron('0 9,10,11,16 * * *')
    //     //pollSCM 'H/10 * * * *'
    // }
    environment {
        CHATID="-481038264"
        TOKEN="1282407535:AAGyfDed5L_R7QLzRkXjX_yPJsGLXUaAn4E"
    }    
    parameters {
        string(name: 'DESCRIPTION', defaultValue: '', description: 'Build description')

        choice(
            choices:['WO_sand_prod','WO_Sandbox', 'WO_Production','Filter_Sort_in_tables','Fleet_Provider_insptction' ],
            description: 'WO_Sandbox -- https://sandbox.driveroo.com/ \n WO_Production -- https://lp.driveroo.com/driveroo \n WO_sand_prod -- https://sandbox.driveroo.com/   https://lp.driveroo.com/driveroo \n Filter_Sort_in_tables -- https://lp.driveroo.com/driveroo \n Fleet_Provider_insptction -- https://lp.driveroo.com/driveroo \n ',
            name: 'ENVIRONMENT')
    }
    stages {
        stage('Git Checkout') {
        	// agent { label 'OD' }
            steps {
                cleanWs()
                // dir("./") {
                    // git branch: 'main', url: 'git@github.com:Slon-ua/WO.git', credentialsId: 'token_github'

// \                    git branch: 'main', url: 'git@github.com:Slon-ua/WO.git', credentialsId: 'd652767c-01b4-4cec-b6bf-aa400521ab9c'
                    // git branch: 'main', url: 'git@github.com:Slon-ua/WO.git', credentialsId: '028be43b-8583-4937-9989-aca8d0628433'

                    // git branch: 'main', url: 'https://github.com/Slon-ua/Drv_WO_Pipeline.git'
                    // sh 'git clone https://github.com/Slon-ua/WO.git ./'

                // }
                sh 'git clone https://github.com/Slon-ua/WO.git ./'
                sh 'uname -a'
                sh 'pwd'
                sh 'ls -la'
                sh 'ls -la Maintenance/'
                
                // sh '/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"'
                // sh '/usr/local/bin/brew -v'

                // sh 'brew install node'
                sh 'ls -la /usr/local/bin/'
                sh 'npm install'

                
                // sh '/usr/local/bin/node -v'
                // sh 'ls -la /usr/local/lib/node_modules/npm/bin/'

                // sh '/usr/local/bin/npm -v'
                // sh '/usr/local/bin/npx -v'
                // sh '/usr/local/lib/node_modules/npm/bin/npm -v'
                // sh '/usr/local/lib/node_modules/npm/bin/npx -v'

                // sh 'curl "https://nodejs.org/dist/latest/node-${VERSION:-$(wget -qO- https://nodejs.org/dist/latest/ | sed -nE 's|.*>node-(.*)\.pkg</a>.*|\1|p')}.pkg" > "$HOME/Downloads/node-latest.pkg" && sudo installer -store -pkg "$HOME/Downloads/node-latest.pkg" -target "/"'

                // sh '/usr/local/bin/npm install'
                // sh 'npm install -g newman-reporter-allure'
                // sh 'date'
                // if (new Date().getHours() <21){
                    // sh 'rm -rf Maintenance/allure-results'

                sh 'ls -la'
                sh 'ls -la Maintenance/'
                // }
                // script {
                //     if (DESCRIPTION != '') {
                //         currentBuild.displayName = "${DESCRIPTION}"
                //     }
                // }
                script {
                    if (DESCRIPTION != '') {
                        currentBuild.displayName = "#${BUILD_NUMBER}, ${params.ActionToRun}, ${params.DESCRIPTION}"
                    }
                }
            }
        }
        stage('Run on WO_Sandbox') {
            when {
                    expression { params.ENVIRONMENT == 'WO_Sandbox' }
            }
            // agent { label 'OD' }
            steps {
                script {
                    try {
                        // sh "curl -s -X POST https://api.telegram.org/bot$TOKEN/sendMessage -d chat_id=$CHATID -d text='Start WO_Sandbox Test.'"
                        sh 'npm run api-WO_Sandbox'
                        // sh "curl -s -X POST https://api.telegram.org/bot$TOKEN/sendMessage -d chat_id=$CHATID -d text='Finish%20 WO_Sandbox %20Test. %0A ${currentBuild.currentResult} %0A https://jenkins.driveroo.com/view/Automation/job/WO_with_and_without_maintenance/"+BUILD_NUMBER+"/allure/'"
                    } catch (Exception err) {
                        echo 'Exception occurred: ' + err.toString()
                        // sh "curl -s -X POST https://api.telegram.org/bot$TOKEN/sendMessage -d chat_id=$CHATID -d text='Finish%20 WO_Sandbox %20Test. %0A ${currentBuild.currentResult} %0A https://jenkins.driveroo.com/view/Automation/job/WO_with_and_without_maintenance/"+BUILD_NUMBER+"/allure/'"
                    }
                }
            }
        }
        stage('Run on WO_Production') {
            when {
                    expression { params.ENVIRONMENT == 'WO_Production' }
            }
            // agent { label 'OD' }
            steps {
                script {
                    try {
                        // sh "curl -s -X POST https://api.telegram.org/bot$TOKEN/sendMessage -d chat_id=$CHATID -d text='Start WO_Production Test.'"
                        sh 'npm run api-WO_Production'
                        // sh "curl -s -X POST https://api.telegram.org/bot$TOKEN/sendMessage -d chat_id=$CHATID -d text='Finish%20 WO_Production %20Test. %0A ${currentBuild.currentResult} %0A https://jenkins.driveroo.com/view/Automation/job/WO_with_and_without_maintenance/"+BUILD_NUMBER+"/allure/'"
                    } catch (Exception err) {
                        echo 'Exception occurred: ' + err.toString()
                        // sh "curl -s -X POST https://api.telegram.org/bot$TOKEN/sendMessage -d chat_id=$CHATID -d text='Finish%20 WO_Production %20Test. %0A ${currentBuild.currentResult} %0A https://jenkins.driveroo.com/view/Automation/job/WO_with_and_without_maintenance/"+BUILD_NUMBER+"/allure/'"
                    }
                }
            }
        }
        stage('Run on WO_sand_prod') {
            when {
                    expression { params.ENVIRONMENT == 'WO_sand_prod' && new Date().getHours() >=10 && new Date().getHours() <21}
            }
            // agent { label 'OD' }
            steps {
                script {
                    try {
                        // sh "curl -s -X POST https://api.telegram.org/bot$TOKEN/sendMessage -d chat_id=$CHATID -d text='Start WO_Sand_Prod Test.'"
                        sh 'npm run api-WO_sand_prod'
                        sh 'npm run api-Fleet_Provider_insptction'
                        // sh "curl -s -X POST https://api.telegram.org/bot$TOKEN/sendMessage -d chat_id=$CHATID -d text='Finish%20 WO_Sand_Prod %20Test. %0A ${currentBuild.currentResult} %0A ${currentBuild.result} %0A https://jenkins.driveroo.com/view/Automation/job/WO_with_and_without_maintenance/"+BUILD_NUMBER+"/allure/'"
                    } catch (Exception err) {
                        echo 'Exception occurred: ' + err.toString()
                        // sh "curl -s -X POST https://api.telegram.org/bot$TOKEN/sendMessage -d chat_id=$CHATID -d text='Finish%20 WO_Sand_Prod %20Test. %0A ${currentBuild.currentResult} %0A ${currentBuild.result} %0A https://jenkins.driveroo.com/view/Automation/job/WO_with_and_without_maintenance/"+BUILD_NUMBER+"/allure/'"
                    }
                }
            }
        } 
        stage('Filter_&_Sort in tables') {
            when {
                    expression { params.ENVIRONMENT == 'Filter_Sort_in_tables' ||  params.ENVIRONMENT == 'WO_sand_prod' && new Date().getHours() <10}
            }
            // agent { label 'OD' }
            steps {
                script {
                    try {
                        // sh "curl -s -X POST https://api.telegram.org/bot$TOKEN/sendMessage -d chat_id=$CHATID -d text='Start Filter__Sort in tables'"
                        sh 'npm run api-Filter_Sort'
                        // sh "curl -s -X POST https://api.telegram.org/bot$TOKEN/sendMessage -d chat_id=$CHATID -d text='Finish%20 Filter__Sort in tables %20Test. %0A ${currentBuild.currentResult} %0A ${currentBuild.result} %0A https://jenkins.driveroo.com/view/Automation/job/WO_with_and_without_maintenance/"+BUILD_NUMBER+"/allure/'"
                    } catch (Exception err) {
                        echo 'Exception occurred: ' + err.toString()
                        // sh "curl -s -X POST https://api.telegram.org/bot$TOKEN/sendMessage -d chat_id=$CHATID -d text='Finish%20 Filter__Sort in tables %20Test. %0A ${currentBuild.currentResult} %0A ${currentBuild.result} %0A https://jenkins.driveroo.com/view/Automation/job/WO_with_and_without_maintenance/"+BUILD_NUMBER+"/allure/'"
                    }
                }
            }
        }
        stage('Run on Fleet_Provider_insptction') {
            when {
                    expression { params.ENVIRONMENT == 'Fleet_Provider_insptction' }
            }
            // agent { label 'OD' }
            steps {
                script {
                    try {
                        // sh "curl -s -X POST https://api.telegram.org/bot$TOKEN/sendMessage -d chat_id=$CHATID -d text='Start Fleet_Provider_insptction Test.'"
                        sh 'npm run api-Fleet_Provider_insptction'
                        // sh "curl -s -X POST https://api.telegram.org/bot$TOKEN/sendMessage -d chat_id=$CHATID -d text='Finish%20 Fleet_Provider_insptction %20Test. %0A ${currentBuild.currentResult} %0A ${currentBuild.result} %0A https://jenkins.driveroo.com/view/Automation/job/WO_with_and_without_maintenance/"+BUILD_NUMBER+"/allure/'"            
                    } catch (Exception err) {
                        echo 'Exception occurred: ' + err.toString()
                        // sh "curl -s -X POST https://api.telegram.org/bot$TOKEN/sendMessage -d chat_id=$CHATID -d text='Finish%20 Fleet_Provider_insptction %20Test. %0A ${currentBuild.currentResult} %0A ${currentBuild.result} %0A https://jenkins.driveroo.com/view/Automation/job/WO_with_and_without_maintenance/"+BUILD_NUMBER+"/allure/'"
                    }
                }
            }
        }
        // finally {
            stage('Reports') {
            	// agent { label 'OD' }
                steps {
                    allure([
                        includeProperties: false,
                        jdk: '',
                        properties: [],
                        reportBuildPolicy: 'ALWAYS',
                        results: [[path: 'Maintenance/allure-results']]
                    ])
                }
            }
        // }

        
        //  sh "curl -s -X POST https://api.telegram.org/bot$TOKEN/sendMessage -d chat_id=$CHATID -d text=\"Build MySQL Sandbox Fleet started.\""

        //  sh "curl -s -X POST https://api.telegram.org/bot1282407535:AAGyfDed5L_R7QLzRkXjX_yPJsGLXUaAn4E/sendMessage -d chat_id=-481038264 -d text='Finish%20Analitics%20script.%0ASand:%0Ahttps://jenkins.driveroo.com/view/Automation/job/Analytics/"+BUILD_NUMBER+"/execution/node/3/ws/sand.html%0AProd:%0Ahttps://jenkins.driveroo.com/view/Automation/job/Analytics/"+BUILD_NUMBER+"/execution/node/3/ws/prod.html'"
        //  sh "curl -s -X POST https://api.telegram.org/bot1282407535:AAGyfDed5L_R7QLzRkXjX_yPJsGLXUaAn4E/sendMessage -d chat_id=-481038264 -d text='Finish%20Analitics%20script.%0ASand:%0Ahttps://jenkins.driveroo.com/view/Automation/job/Analytics/"+BUILD_NUMBER+"/execution/node/3/ws/sand.html'"

        //  sh "curl -s -X POST https://api.telegram.org/bot1282407535:AAGyfDed5L_R7QLzRkXjX_yPJsGLXUaAn4E/sendMessage -d chat_id=-481038264 -d text='Finish%20API%20Test.%0Ahttps://jenkins.driveroo.com/job/Postman_API_Pipeline/lastBuild/consoleText'"
        //  sh "curl -s -X POST https://api.telegram.org/bot1282407535:AAGyfDed5L_R7QLzRkXjX_yPJsGLXUaAn4E/sendMessage -d chat_id=-481038264 -d text='Finish%20API%20Test.%0A https://jenkins.driveroo.com/view/Automation/job/WO_with_and_without_maintenance/"+BUILD_NUMBER+"/console'"
    }
}
