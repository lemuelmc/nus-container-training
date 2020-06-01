FROM mysql:5.7

# Set MySQL root password
ENV MYSQL_ROOT_PASSWORD=changeit MYSQL_DATABASE=northwind 

# Copy sql schema to /docker-entrypoint-initdb.d
ADD 0-northwind-default-current-timestamp.sql /docker-entrypoint-initdb.d
ADD 1-northwind-data.sql /docker-entrypoint-initdb.d

# Add health check
HEALTHCHECK --interval=30s --timeout=30s --start-period=15s --retries=3 \
    CMD mysqladmin ping -uroot -p${MYSQL_ROOT_PASSWORD}

EXPOSE 3306
VOLUME /var/lib/mysql