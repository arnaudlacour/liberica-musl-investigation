# liberica-musl-investigation
This project is intended to make investigating an issue with 
BellSoft liberica OpenJDK on Alpine with the musl libc where 
calls to ProcessBuilder may hang indefinitely with PingData 
products

To further qualify this, we see this occur 100% of the time
with PingData but about 1/3 of the time when starting DropWizard.

# Workaround
use `-Djdk.lang.Process.launchMechanism=POSIX_SPAWN`

# How to use this
  ## prepare
```  
curl -O https://raw.githubusercontent.com/arnaudlacour/liberica-musl-investigation/master/docker-compose.yaml
```

  ## To demonstrate the work around
```  
KEY=<DEVOPS KEY> MODE="good" docker-compose up --exit-code-from pingdirectory --abort-on-container-exit

docker-compose down
```
  ## To reproduce the issue
```  
KEY=<DEVOPS KEY> MODE="bug" docker-compose up --exit-code-from pingdirectory --abort-on-container-exit

docker-compose down
```
