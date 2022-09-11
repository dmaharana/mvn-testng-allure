JP = [
    // sourceUrl: 'git@github.com:dmaharana/mvn-testng-allure-example.git',
    sourceUrl: 'git@github.com:dmaharana/mvn-testng-allure.git',
    gitBranch: GIT_BRANCH_NAME,
    repoName: 'mvn-testng-allure-example',
    testRunCmd: 'mvn clean test',
    allureReportCmd: 'allure generate --clean',
    allureTestResultFolder: 'allure-results',
]
node('buildnode') {
    Clean_ws()
    try {
        stage('Testing') {
            Preparation_stage(JP)
        }
        stage('Testing') {
            RunTests_stage(JP)
        }
    } finally {
        echo "Publish Allure Report"
        dir (JP.repoName) {
            sh JP.allureReportCmd

            allure([
                includeProperties: false,
                jdk: '',
                properties: [],
                reportBuildPolicy: 'ALWAYS',
                results: [[path: JP.allureTestResultFolder]]
            ])
        }
        // Clean_ws()
    }
}

def Preparation_stage(JP) {
    echo "Entering Preparation stage"
    sh "git clone ${JP.sourceUrl} -b ${JP.gitBranch} --depth 1 ${JP.repoName}"
    echo "Exiting Preparation stage"
}

def RunTests_stage(JP) {
    echo "Entering Run Test stage"
    dir (JP.repoName) {
        sh JP.testRunCmd
    }
    echo "Exiting Run Test stage"
}

def Clean_ws() {
    cleanWs(cleanWhenNotBuilt: false,
                deleteDirs: true,
                disableDeferredWipeout: true,
                notFailBuild: true)
}