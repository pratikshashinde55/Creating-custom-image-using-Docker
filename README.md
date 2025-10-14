# *Docker Custom Image Creation*

---

### **Purpose of Creating a Custom Image**

Custom images are used when containers require multiple specific configurations, packages, or settings.

> In the container ecosystem, we **share images**, not containers.

---

### **Two Methods to Create a Custom Docker Image**

### **Method 1 – Using `docker commit` Command**

In this method:

1. Start a container from a base image.
2. Make your required changes inside the container (e.g., install software, change settings).
3. Create a new image from that modified container.


**Example:**

* Create a container and modify it as needed.
* Commit the changes to a new custom image:

```bash
docker commit commit1 myos1:v1
```
<img width="725" height="159" alt="Screenshot 2025-09-15 235053" src="https://github.com/user-attachments/assets/3340716c-4934-4789-9cd0-5f99d4da7c93" />
<img width="988" height="81" alt="Screenshot 2025-09-15 235247" src="https://github.com/user-attachments/assets/8241d6d2-2fb8-4a84-9ce1-fed1af725d5d" />

* Run a container from the custom image:

```bash
docker run -it --name mycontainer myos1:v1
```
<img width="887" height="104" alt="Screenshot 2025-09-15 235319" src="https://github.com/user-attachments/assets/89a20dd1-81ce-4ffd-8afc-109bf3e6b688" />

---

### **Method 2 – Using Dockerfile (`docker build`)**

This is a code-based, fully automated method to create custom images using a **Dockerfile**.
<img width="392" height="133" alt="Screenshot 2025-10-14 210842" src="https://github.com/user-attachments/assets/2a1d6a75-c3a4-44a0-8095-cf9e8a9b77a4" />


#### **Dockerfile**

A plain text file containing instructions to build an image.
Create Dockerfile:

<img width="431" height="378" alt="Screenshot 2025-10-14 211743" src="https://github.com/user-attachments/assets/4172a92d-a6ab-471c-9e35-5bddcb48080a" />
<img width="519" height="110" alt="Screenshot 2025-10-14 210857" src="https://github.com/user-attachments/assets/46a572c1-43b0-4b51-8f18-4dd42ab1dc49" />

**Example build command (from current directory):**

```bash
docker build -t myapp:latest
```
<img width="1414" height="457" alt="Screenshot 2025-10-14 211730" src="https://github.com/user-attachments/assets/9d5b2d99-b956-4d0f-a99a-6b7699aee3b9" />


**Build from a specific file and directory:**

```bash
example;  docker build -t myimage:v1 -f myYmlcode /mybuildcode/
```

**Explanation:**

* `-t` → Tags the image with a name and version.
* `-f` → Specifies the filename of the Dockerfile.
* `.` → Refers to the build context (current directory).

---

### **Important Dockerfile Keywords:**

* `FROM` → Specifies the base image.
* `RUN` → Executes commands during the image build (e.g., installing packages).


### **Build and Run Custom Image**

* **Build the image from Dockerfile:**

```bash
docker build -t myimage:v1 .
```
<img width="790" height="132" alt="Screenshot 2025-09-15 235831" src="https://github.com/user-attachments/assets/5eb8316d-4d9f-4973-a632-5bc65ceab29f" />

* **Run a container from the custom image:**

```bash
 docker run myapp
```
<img width="730" height="157" alt="Screenshot 2025-10-14 211828" src="https://github.com/user-attachments/assets/7e7afb19-49b5-44fd-a145-72dff8456104" />


---

***Now push created image to docker hub:***

Go to Docker Hub registry->create account->go to registry->create registry as "myapp"
<img width="1858" height="494" alt="Screenshot 2025-10-14 212739" src="https://github.com/user-attachments/assets/c9d1b6dd-37e3-4c52-9403-47b4b376703d" />

1.Docker login->Provide username and password.
<img width="1872" height="369" alt="Screenshot 2025-10-14 211928" src="https://github.com/user-attachments/assets/d80887b5-14d0-44af-9438-e7f7ca5fd195" />
2.
Look for image and tag it 

docker images

docker tag myapp:latest pratikshash67/myapp:latest

<img width="904" height="292" alt="Screenshot 2025-10-14 212116" src="https://github.com/user-attachments/assets/121bd675-e523-4b85-bd8d-3fdf610700f6" />
3.Push the image to Dockerhub registry

docker push pratikshash67/myapp:latest
<img width="904" height="292" alt="Screenshot 2025-10-14 212116" src="https://github.com/user-attachments/assets/8f9830d8-3b11-4a39-9df6-9971ca38b540" />

<img width="1116" height="270" alt="Screenshot 2025-10-14 213523" src="https://github.com/user-attachments/assets/6dcaf406-cbf5-46bd-aafe-1dde5b42d3a3" />

<img width="1882" height="753" alt="image" src="https://github.com/user-attachments/assets/f2e9e5e6-0384-4c2f-a7fb-76da446d8a8a" />

### **About**

This section demonstrates how to create Docker custom images using two methods:

* `docker commit` command (manual)
* `docker build` command with Dockerfile (automated)

---

