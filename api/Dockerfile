FROM python:3.11-slim

# Set the working directory in the container
WORKDIR /usr/scr/app


# Copy the dependencies file to the working directory
COPY requirements.txt ./

# Install any dependencies
RUN pip install --no-cache-dir -r requirements.txt


#Copy the content of the local src directory to the working directory or copy main.py ./ would be enough for this simple example
COPY . . 


# Run the application:
CMD ["uvicorn", "main:app", "--host", "0.0.0.0", "--port", "80"]
