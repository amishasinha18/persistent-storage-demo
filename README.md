# Docker Persistent Storage Demo

A simple Docker project that demonstrates how to use a **Docker Volume** to keep application data persistent even after a container is deleted.

## 📌 About

Docker containers are temporary by nature. If data is stored only inside a container, it can be lost when the container is removed.

In this project, a named Docker Volume called **`appdata`** is used as persistent storage. The Python application stores data in **`/data/uploads.txt`**.

### How it works

```text
Python Application
        ↓
      /data
        ↓
Docker Volume: appdata
        ↓
   Persistent Data
🛠️ Technologies Used
Python 3.11
Docker
Docker Volume
📂 Project Structure
persistent-storage-demo/
│
├── app.py
├── Dockerfile
└── README.md
🚀 How to Run
1. Build the Docker Image
docker build -t persistentapp:v1 .
2. Create a Docker Volume
docker volume create appdata
3. Run the Container with the Volume
docker run --name mypersistentcontainer -v appdata:/data persistentapp:v1

The application writes the data to:

/data/uploads.txt
🔄 Test Data Persistence

Remove the container:

docker rm -f mypersistentcontainer

Create a new container using the same volume:

docker run --name mypersistentcontainer2 -v appdata:/data persistentapp:v1

The previously stored data will still be available.

This proves that the data is stored in the Docker Volume, not only inside the container.

🔍 Verification

To inspect the Docker Volume:

docker volume inspect appdata

To inspect the container and its mounted volume:

docker inspect mypersistentcontainer2
✅ Result

The project successfully demonstrates persistent storage in Docker using a named volume. Application data remains available even after the original container is removed and a new container is created using the same volume.

📚 Learning Outcomes
Understand why container data can be temporary.
Create and use a Docker Volume.
Mount a volume to a container.
Store application data in persistent storage.
Verify data persistence after container deletion.