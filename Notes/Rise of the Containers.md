https://riseofthecontainers.github.io/docker/01-why/

https://riseofthecontainers.github.io/docker/

# Rise of the Containers

## Virtual Machine Model

1.  Host Operating System Layer
    1.  Machine
2.  Hypervisor(virtualization) Layer
    1.  Give ability to run VM on top of host operating system - does translations
3.  VM Layer
    1.  Contains
        \- Guest Operating Sysem
        \- Software (java, db,)
        \- Deployed application
    2.  Can run mulitple VMs each can have thier own operating systems
4.  Challenges with Virtual Machine Model
    1.  Resource Utilization
        \- CPU, RAM, Disk consumed by Guest OS
    2.  Performance Overhead
        - Multiple OS + hypervisor translation layer
    3.  Cost Overhead
        \- Software licenses (Guest OS0 (capex)
        \- Each VM Maintenance & Upgrade/Patching cost (opex)
        ![Screen Shot 2023-06-02 at 12.16.25 PM.png](../_resources/Screen%20Shot%202023-06-02%20at%2012.16.25%20PM-1.png)

## Container Model

1.  Run VM without the Guest OS,
    1.  Host OS Layer
    2.  Container Runtime (engine) Layer (LXC or Linux)
2.  Container Philosophy
    1.  CGroups - allows limitation and prioritization of resources (CPU, memory, block I/O, network, ect.)
    2.  Namespace Isolation - Allows complete isolation of applications' view of the operation envoirment
 ![Screen Shot 2023-06-02 at 12.19.58 PM.png](../_resources/Screen%20Shot%202023-06-02%20at%2012.19.58%20PM-1.png)
3.  Container packaging 
	1.  app.jar - zip format packaging of all class files 
	2.  .war - file contains app.jar files and dependant jar files
	3.  .ear - Enterprise Archive - contains .war files 
		1.  deploy multiple web applications together 
![Screen Shot 2023-06-02 at 12.26.52 PM.png](../_resources/Screen%20Shot%202023-06-02%20at%2012.26.52%20PM-1.png)
## Docker 
### Docker Architechture
1. Client Server Arch,
2. Docker Host 
	1. Has a runtime (docker daemon, manage and run containers)
		1. Controlled by Docker CLI(Client)
		2. Images / Artifacts stored in Docker Registry 
### Docker Commands 
1. Create container with image 
```
docker run -d nginx
```
2. Port forwarding = Connect to port > redirect my docker port to local machine port 
	1. --name - give container a name -d run in detached mode
	2. connnect to port 80:80
```
docker run -p 80:80 --name myweb -d nginx 
```
3. Can run curl command to see response (cURL == client URL) - used to talk to server by specifying location
```
curl localhost:80
```
4. Go inside the container -it == interactive , sh == shell 
```
docker exec -it myweb sh 
```

```
docker exec -it myweb /bin/bash
```

![Screen Shot 2023-06-04 at 1.45.17 PM.png](../_resources/Screen%20Shot%202023-06-04%20at%201.45.17%20PM-1.png)
![Screen Shot 2023-06-04 at 1.45.45 PM.png](../_resources/Screen%20Shot%202023-06-04%20at%201.45.45%20PM-1.png)

