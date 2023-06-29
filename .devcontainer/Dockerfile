# Use an existing docker image where Godot is installed
FROM godotengine/godot:latest

# The docker user that you want, change the uid and gid as needed
RUN useradd -m godotdev --uid=1000 && echo "godotdev:godotdev" | chpasswd && adduser godotdev sudo

# Switch to the new user
USER godotdev

# Set the working directory
WORKDIR /home/godotdev

# Run the command on container startup
CMD ["bash"]
