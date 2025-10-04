# *Docker Custom Image Creation*

---

### **Purpose of Creating a Custom Image**

Custom images are used when containers require multiple specific configurations, packages, or settings.

> In the container ecosystem, we **share images**, not containers.

---

### **Two Methods to Create a Custom Docker Image**

---

### **Method 1 – Using `docker commit` Command**

In this method:

1. Start a container from a base image.
2. Make your required changes inside the container (e.g., install software, change settings).
3. Create a new image from that modified container.
<img width="725" height="159" alt="Screenshot 2025-09-15 235053" src="https://github.com/user-attachments/assets/3340716c-4934-4789-9cd0-5f99d4da7c93" />

**Example:**

* Create a container and modify it as needed.
* Commit the changes to a new custom image:

```bash
docker commit commit1 myos1:v1
```
<img width="988" height="81" alt="Screenshot 2025-09-15 235247" src="https://github.com/user-attachments/assets/8241d6d2-2fb8-4a84-9ce1-fed1af725d5d" />

* Run a container from the custom image:

```bash
docker run -it --name mycontainer myos1:v1
```
<img width="887" height="104" alt="Screenshot 2025-09-15 235319" src="https://github.com/user-attachments/assets/89a20dd1-81ce-4ffd-8afc-109bf3e6b688" />

---

### **Method 2 – Using Dockerfile (`docker build`)**

This is a code-based, fully automated method to create custom images using a **Dockerfile**.
<img width="642" height="238" alt="Screenshot 2025-09-15 235720" src="https://github.com/user-attachments/assets/dcee6932-9cb0-40b1-adb9-7a8f198b7022" />
<img width="539" height="437" alt="Screenshot 2025-09-15 235659" src="https://github.com/user-attachments/assets/a69befcf-903c-4fd6-abe9-d2a8797eaa80" />

#### **Dockerfile**

A plain text file containing instructions to build an image.

**Example build command (from current directory):**

```bash
docker build -t myimage:v1 .
```
<img width="1165" height="440" alt="Screenshot 2025-09-15 235839" src="https://github.com/user-attachments/assets/7e4631ba-b225-4d29-b7b9-52e9373ce8bb" />


**Build from a specific file and directory:**

```bash
docker build -t myOwnimage:v1 -f myYmlcode /mycodefolder/
```

**Explanation:**

* `-t` → Tags the image with a name and version.
* `-f` → Specifies the filename of the Dockerfile.
* `.` → Refers to the build context (current directory).

---

### **Important Dockerfile Keywords:**

* `FROM` → Specifies the base image.
* `RUN` → Executes commands during the image build (e.g., installing packages).

> Always use non-interactive commands in Dockerfiles. For example:

```Dockerfile
RUN yum install httpd -y
```

---

### **Build and Run Custom Image**

* **Build the image from Dockerfile:**

```bash
docker build -t myimage:v1 .
```
<img width="790" height="132" alt="Screenshot 2025-09-15 235831" src="https://github.com/user-attachments/assets/5eb8316d-4d9f-4973-a632-5bc65ceab29f" />

* **Run a container from the custom image:**

```bash
docker run -it --name myos1 myimage:v1
```
<img width="1679" height="143" alt="Screenshot 2025-09-15 235949" src="https://github.com/user-attachments/assets/99b03dfc-3d3a-49f9-ab14-c577e39072c5" />


---

### **About**

This section demonstrates how to create Docker custom images using two methods:

* `docker commit` command (manual)
* `docker build` command with Dockerfile (automated)

---

