# Use the pre-built base image for A0
FROM agent-zero-base:local
# FROM frdel/agent-zero-base:latest

# Copy contents of the project to /a0
COPY ./docker/base/fs/ /
COPY ./docker/run/fs/ /

# Install python requirements
COPY ./requirements.txt /a0/requirements.txt
RUN /opt/venv/bin/pip install -r /a0/requirements.txt

# install additional software
RUN bash /ins/install_additional.sh

# post installation steps
RUN bash /ins/post_install.sh

# Expose ports
EXPOSE 22 80 9000-9009

RUN chmod +x /exe/initialize.sh /exe/run_A0.sh /exe/run_searxng.sh /exe/run_tunnel_api.sh

# initialize runtime and switch to supervisord
CMD ["/exe/initialize.sh", "main"]
