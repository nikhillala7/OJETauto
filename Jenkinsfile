// node {
//       stage("checkout") {
//         git url: 'https://github.com/jenkinsci/last-changes-plugin.git'
//       }

//       stage("last-changes") {
//         def publisher = LastChanges.getLastChangesPublisher "LAST_SUCCESSFUL_BUILD", "SIDE", "LINE", true, true, "", "", "", "", ""
//               publisher.publishLastChanges()
//               def changes = publisher.getLastChanges()
//               println(changes.getEscapedDiff())
//               for (commit in changes.getCommits()) {
//                   println(commit)
//                   def commitInfo = commit.getCommitInfo()
//                   println(commitInfo)
//                   println(commitInfo.getCommitMessage())
//                   println(commit.getChanges())
//               }
//       }

// }
// node() {
//   passedBuilds = []

//   lastSuccessfulBuild(passedBuilds, currentBuild);

//   def changeLog = getChangeLog(passedBuilds)
//   echo "changeLog ${changeLog}"
// }

// def lastSuccessfulBuild(passedBuilds, build) {
//   if ((build != null) && (build.result != 'SUCCESS')) {
//       passedBuilds.add(build)
//       lastSuccessfulBuild(passedBuilds, build.getPreviousBuild())
//    }
// }

// @NonCPS
// def getChangeLog(passedBuilds) {
//     def log = ""
//     for (int x = 0; x < passedBuilds.size(); x++) {
//         def currentBuild = passedBuilds[x];
//         def changeLogSets = currentBuild.rawBuild.changeSets
//         for (int i = 0; i < changeLogSets.size(); i++) {
//             def entries = changeLogSets[i].items
//             for (int j = 0; j < entries.length; j++) {
//                 def entry = entries[j]
//                 log += "* ${entry.msg} by ${entry.author} \n"
//             }
//         }
//     }
//     return log;
//   }
pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/jenkinsci/last-changes-plugin.git'
                lastChanges since: 'LAST_SUCCESSFUL_BUILD', format:'SIDE',matching: 'LINE'
            }
        }
    }
}
