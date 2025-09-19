# Use an official Python runtime as a parent image
FROM python:3.12-slim-trixie

LABEL version='V1' description="First flask image"

# Set the working directory in the container
WORKDIR /my-rest-api

# Copy the requirements.txt file into the container
COPY requirements.txt .

# Install any needed packages specified in requirements.txt
RUN pip install --no-cache-dir -r requirements.txt

# Copy the rest of the application code into the container
COPY . .

# Expose the port on which the Flask app will run (default is 5000)
EXPOSE 5000

# Define the command to run the Flask application
CMD ["python", "src/app.py"]
