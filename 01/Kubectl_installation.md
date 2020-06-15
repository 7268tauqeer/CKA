Download Binary:
curl -LO https://storage.googleapis.com/kubernetes-release/release/`curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt`/bin/linux/amd64/kubectl

change permisson:
chmod +x kubectl

move to local binaries:
move kubectl /usr/local/bin

Configure authentication for kubectl:
mkdir ~/.kube
cd ./kube
touch config

update config file with necessary info i.e. context key crt role etc.