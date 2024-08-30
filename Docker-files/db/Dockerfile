FROM mysql:8.0.33
LABEL "Project"="Vprofile"
LABEL "Author"="Quan"

# we will override this variable later. Defining MYSQL_ROOT_PASSWORD in Dockerfile sets the default password during image build, while defining it in docker-compose.yml provides a default for Docker Compose, allowing users to override it if needed.
ENV MYSQL_ROOT_PASSWORD="vprodbpass"
# when the container come up, it will create a "accounts" database
ENV MYSQL_DATABASE="accounts"

ADD db_backup.sql /docker-entrypoint-initdb.d/db_backup.sql
# ADD db_backup.sql docker-entrypoint-initdb.d/db_backup.sql