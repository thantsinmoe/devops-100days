Task : Create user, database and grant all permission for user

cmd >> sudo -i -u postgres                                              #Switch to the postgres user 
cmd >> psql                                                             #access the psql
cmd >> CREATE USER kodekloud_top WITH PASSWORD 'ksH85UJjhb';            
cmd >> CREATE DATABASE kodekloud_db8;
cmd >> GRANT ALL PRIVILEGES ON DATABASE kodekloud_db8 TO kodekloud_top;