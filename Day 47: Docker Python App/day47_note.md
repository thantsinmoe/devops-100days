Task:
1. Create a Dockerfile under /python_app directory:

2. Use any python image as the base image.
    Install the dependencies using requirements.txt file.
    Expose the port 8086.
    Run the server.py script using CMD.

3. Build an image named nautilus/python-app using this Dockerfile.

Once image is built, create a container named pythonapp_nautilus:
Map port 8086 of the container to the host port 8095.

# Create Dockefile
cd /python_app/
vi Dockerfile
  # Dockerfile
    #Base Image
    FROM python:3.10-alpine   

    #Work Direcotry
    WORKDIR /app

    #Copy requirements
    COPY src/requirements.txt .

    #Install dependencies
    RUN pip3 install --no-cache-dir -r requirements.txt

    #Copy source file 
    COPY src/ .

    #Port Expose
    EXPOSE 8086

    #Run cmd
    CMD [ "python3", "server.py" ]

# Build docker image and run container
docker build -t nautilus/python-app .
docker run -d --name pythonapp_nautilus -p 8095:8086 nautilus/python-app:latest
curl http://localhost:8095/