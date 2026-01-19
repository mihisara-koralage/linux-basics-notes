# Day 27 – Docker Volumes & Data Persistence
## Why Containers Lose Data?
Containers are temporary by design.

If you:
- Stop container 
- Remove container 

All data inside is lost
## Volume commands
A volume is:
- Storage outside the container
- Managed by Docker
- Survives container deletion

Think of it as:
“Hard disk attached to container”

List Volumes:
```
sudo docker volume ls
```
Create Volume:
```
sudo docker volume create my-volume
```
Check:
```
sudo docker volume inspect my-volume
```
Use Volume with Container:
```
sudo docker run -it --name vol-test \
-v my-volume:/data \
ubuntu
```
Inside container:
```
cd /data
echo "Hello Volume" > test.txt
exit
```
Remove Container:
```
sudo docker rm vol-test
```
Run New Container with SAME Volume:
```
sudo docker run -it --name vol-test2 \
-v my-volume:/data \
ubuntu
```
Inside:
```
cat /data/test.txt
```
Data is still there.

Remove Volume:
```
sudo docker volume rm my-volume
```
## Why volumes are critical
| Use Case  | Why Volume     |
| --------- | -------------- |
| Databases | Persist data   |
| Logs      | Debug crashes  |
| Uploads   | User files     |
| Config    | Shared configs |
