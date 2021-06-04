# liberica-musl-investigation
This project is intended to make investigating an issue with 
BellSoft liberica OpenJDK on Alpine with the musl libc where 
calls to ProcessBuilder may hang indefinitely with PingData 
products

To further qualify this, we see this occur 100% of the time
with PingData but about 1/3 of the time when starting DropWizard.
