FROM podiobooks/podiobooks-centos-base

MAINTAINER Tim L. White "tim@podiobooks.com"

# Update the OS
RUN yum update -y --nogpgcheck && yum upgrade -y --nogpgcheck

# Install Prereqs
RUN yum install -y libxslt uuid

# Install PostgreSQL
RUN yum install -y postgresql-server postgresql-libs postgresql-contrib postgresql-devel --disablerepo=* --enablerepo=postgresql

# Add Postgres User to podiobooks Group
RUN usermod -G podiobooks postgres

# Switch to postgres user
USER postgres

# Add postgres init file
ADD postgres-initial-setup.sh /opt/podiobooks/postgres-initial-setup.sh

# Expose Ports
EXPOSE 5432

# Start Postgres When Container Starts By Default
CMD ["/usr/pgsql-9.3/bin/postgres", "-D", "/opt/podiobooks/data/db/"]
