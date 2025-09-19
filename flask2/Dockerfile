# Stage 1: Build Stage
FROM python:3.12-slim-trixie AS builder

WORKDIR /my-rest-api

# Copy requirements.txt and install dependencies
COPY requirements.txt .

# Install any needed packages specified in requirements.txt
RUN pip install --no-cache-dir -r requirements.txt

# Check packages path exists
RUN ls -lR /usr/local/lib/python3.12/site-packages

# Copy application code
COPY . .

# Stage 2: Production Image
FROM python:3.12-slim-trixie AS final

WORKDIR /my-rest-api

# Check packages path exists
RUN ls -lR /usr/local/lib/python3.12/site-packages

# Copy only necessary files from the builder stage
COPY --from=builder /usr/local/lib/python3.12/site-packages /usr/local/lib/python3.12/site-packages
COPY --from=builder /my-rest-api/src ./src

# Expose the port Flask runs on
EXPOSE 5000

# Command to run the Flask application
CMD ["python", "src/app.py"]