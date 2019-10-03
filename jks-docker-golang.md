## How to securely pass ssh private key to GO Build Pipeline

This example resolves the challenge How to securely pass private key to GO Build Pipeline

### Problem to resolve: 

Currently my-app-micro-service has multiple modules built by GO, in order to build them by Jenkins pipeline, we need to pass the value of Private key to Dockerfile as Build ARG, which is insecure.

### Solution:

#1: Build a tmp key vault container can be accessed from inside the Jenkins server, which allows dockerfile to download the key file during build and kill this tmp container right after build. 

#2: Always use multi-stage build, and access this tmp key server only at the first stage, then copy the build to next stage and remove this first stage container.

### Working Environments and Tools:
```
Jenkins:jenkinsfile
Dockerfile
Bash script
httpd
GO GET
GO Build

```
Details are documented in another repo:

https://github.com/jimmycgz/DevSecOps/edit/master/Own-Key-Vault.md
