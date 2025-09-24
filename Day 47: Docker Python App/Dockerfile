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



