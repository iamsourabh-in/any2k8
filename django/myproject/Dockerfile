# Use the official Python image as the base image
FROM python:3.0

# Set the working directory in the container
WORKDIR /app

# Copy the requirements.txt file into the container
COPY requirements.txt .

# Install the Python dependencies
RUN pip install -r requirements.txt

# Copy the rest of your project files into the container
COPY . .

# Expose the port your Django app will run on
EXPOSE 8000

# Command to run your Django application
CMD ["python", "manage.py", "runserver", "0.0.0.0:8000"]
