# Jenkins

Jenkins LTS with JDK 21 and Docker-in-Docker support.

## Usage
```bash
vagrant up
# Wait ~2 minutes for Jenkins to initialize
```

| | |
|---|---|
| IP | 192.168.56.80 |
| UI | http://192.168.56.80:8080 |
| Also | http://localhost:8084 (port forward) |
| JNLP agent port | 50000 |

## Get initial admin password
```bash
vagrant ssh -c "sudo cat /opt/jenkins/secrets/initialAdminPassword"
```

## Setup
1. Open UI and enter the initial password
2. Install suggested plugins
3. Create admin user

## Docker in pipelines
The Docker socket is mounted — pipelines can run `docker build` and `docker run` directly.

```groovy
pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh 'docker build -t myapp .'
      }
    }
  }
}
```

## Connect another Vagrant VM as an agent
On the agent VM install Java 21 and add it as a **Permanent Agent** in Jenkins:
- **Remote root directory**: `/home/vagrant/agent`
- **Launch method**: SSH
- **Host**: `192.168.56.XX`
