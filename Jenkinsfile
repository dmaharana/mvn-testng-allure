JP = [
    sourceUrl: 'git@github.com:dmaharana/mvn-testng-allure-example.git',
    gitBranch: GIT_BRANCH_NAME,
    repoName: 'mvn-testng-allure-example',
    testRunCmd: 'mvn clean test && allure generate --clean',
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
        Clean_ws()
    }
}

def Preparation_stage(JP) {
    sh "git clone ${JP.sourceUrl} -b ${JP.gitBranch} --depth 1 ${JP.repoName}"
}

def RunTests_stage(JP) {
    dir (JP.repoName) {
        sh JP.testRunCmd

        allure([
            includeProperties: false,
            jdk: '',
            properties: [],
            reportBuildPolicy: 'ALWAYS',
            results: [[path: JP.allureTestResultFolder]]
        ])
    }
}

def Clean_ws() {
    cleanWs(cleanWhenNotBuilt: false,
                deleteDirs: true,
                disableDeferredWipeout: true,
                notFailBuild: true)
}