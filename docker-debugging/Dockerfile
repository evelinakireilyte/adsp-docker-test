# Start with Python base image -> had to beupdated as did not exist
FROM python:3.11.0-slim
WORKDIR /app

# Install dependencies -> requirements folder had to be created first
RUN mkdir /requirements
COPY requirements.txt /requirements/
RUN pip3 install -r /requirements/requirements.txt

# Copy the source code into the /app directory -> had to specify dir to copy to: /app
COPY /src/. /app

# Create a non-root user -> user is called appuser
RUN groupadd -g 2222 appuser
RUN useradd -m -u 2222 --gid 2222 appuser

RUN chown -R appuser:appuser /app

USER appuser
# Specify the port number the container should expose
EXPOSE 8000

# Set entrypoint to run the application -> as the comment suggests it is an antrypoint, not CMD
ENTRYPOINT ["./run.sh"]