## Base Image 
FROM python:3.9-slim 

## Worker DIR / Set Current WorkDir
WORKDIR /app 

## Copy the App. Code inside Workdir 
COPY . /app

## Install the Python Flask Package 
RUN pip install --no-cache-dir -r req.txt 

## Execute the App Code
CMD ["python", "app.py"]  
