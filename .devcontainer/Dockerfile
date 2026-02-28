FROM node:22

# Install basic development tools and PostgreSQL
RUN apt update && apt install -y less man-db sudo postgresql postgresql-contrib

# Ensure default `node` user has access to `sudo`
ARG USERNAME=node
RUN echo $USERNAME ALL=\(root\) NOPASSWD:ALL > /etc/sudoers.d/$USERNAME \
    && chmod 0440 /etc/sudoers.d/$USERNAME

# Initialize PostgreSQL and set password for postgres user
RUN service postgresql start \
    && su -c "psql -c \"ALTER USER postgres WITH PASSWORD 'postgres';\"" postgres \
    && service postgresql stop

# Set `DEVCONTAINER` environment variable to help with orientation
ENV DEVCONTAINER=true
