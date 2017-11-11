node {
    stage 'checkout'
    checkout scm

    stage 'build'
    if (isUnix()) {
        sh './gradlew clean build'
    } else {
        bat './gradlew.bat clean build'
    }

    stage 'test'
    if (isUnix()) {
        sh './gradlew test'
    } else {
        bat './gradlew.bat test'
    }
    step([$class: 'JUnitResultArchiver', testResults: '**/build/test-results/**/TEST-*.xml'])

    stage: 'postbuild'
    if (isUnix()) {
        sh 'ls -la'
    } else {
        bat 'dir'
    }
}