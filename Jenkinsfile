
node {

stage("Checkout") {
    parallel chrome: {
        node('master') {
           git 'https://github.com/duotechacademy/JenkinsCrossBrowserParallelTestingCucumberFramework' 
        }
    },
    edge: {
        node('linux') {
           git 'https://github.com/duotechacademy/JenkinsCrossBrowserParallelTestingCucumberFramework' 
  
        }
    },
    headlessChrome: {
        node('mac') {
           git 'https://github.com/duotechacademy/JenkinsCrossBrowserParallelTestingCucumberFramework' 
  
        }
    }
    
    
}

stage("Build and Test") {
    parallel chrome: {
        node('master') {
             bat label: '', script: 'mvn verify -Dbrowser="chrome"' 
        }
    },
    edge: {
        node('linux') {
             bat label: '', script: 'mvn verify -Dbrowser="edge"' 
        }
    },
    headlessChrome: {
        node('mac') {
             bat label: '', script: 'mvn verify -Dbrowser="headlessChrome"' 
        }
    }
    
    
}

stage("Report") {
    parallel chrome: {
        node('master') {
              junit '**/*Cucumber.xml'  
        }
    },
    edge: {
        node('linux') {
             junit '**/*Cucumber.xml' 
        }
    },
    headlessChrome: {
        node('mac') {
             junit '**/*Cucumber.xml' 
        }
    }
    
    
}


stage("Email") {
    parallel chrome: {
        node('master') {
              step([$class: 'Mailer', notifyEveryUnstableBuild: true, recipients: 'duotechinstructor@gmail.com', sendToIndividuals: false])  
        }
    },
    edge: {
        node('linux') {
            step([$class: 'Mailer', notifyEveryUnstableBuild: true, recipients: 'duotechinstructor@gmail.com', sendToIndividuals: false])  

        }
    },
    headlessChrome: {
        node('mac') {
            step([$class: 'Mailer', notifyEveryUnstableBuild: true, recipients: 'duotechinstructor@gmail.com', sendToIndividuals: false])  

        }
    }
    
    
}

}
