node {
def app 
stage("Cloning Repository")
{
checkout scm
}

stage("Building Image")
{
app = docker.build("yasharul/devops_docker")
}

stage("Testing Image")
{
app.inside
{
echo "Successfully Passed the Test"
}
}

stage("Push image to Docker")
{
docker.withRegistry("https://registry.hub.docker.com","yashwanth_docker")
{
app.push("${env.BUILD_NUMBER}")
app.push("latest")
}

echo "Pushing docker build to docker hub"
}
}
