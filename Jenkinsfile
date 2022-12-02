pipeline {
agent {
label {
label "built-in"
customWorkspace "/mnt/wars/"
}
}

stages {
stage ('clone-project') {
steps {
sh "rm -rf *"
sh "sudo git clone https://github.com/aakashchavhan/game-of-life.git"
sh "sudo chmod -R 777 /mnt"
}
}

stage ('build-project') {
steps {
dir ('/mnt/wars/game-of-life') {
sh "sudo mvn clean install"
sh "sudo cp -r /mnt/wars/game-of-life/gameoflife-web/target/gameoflife.war /mnt/project"
}
}
}

stage ('deployement using ansible') {
steps {
dir ('/mnt/project') {
sh "sudo chmod 777 *"
sh "sudo ansible-playbook play-book.yaml"
}
}
}
}
}
