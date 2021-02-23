--------------Install and Configuiring PostgreSQL--------------
sudo -u postgres psql

CREATE ROLE "dolero-user" WITH LOGIN PASSWORD 'PASS_word'; -- Create user with name "dolero-user" and password "PASS_word"

ALTER ROLE "dolero-user" PASSWORD 'PASS_word_new'; -- Change password at the role "dolero-user"

sudo -u postgres createdb -O dolero-user dolero-base -- Create database with name "dolero-base"

on path /etc/postgresql/10/main/pg_hba.conf write next config "host    dolero-base     dolero-user     all                     md5"

sudo systemctl restart postgresql -- Reload PostgreSQL

----Create phpass----
#формат файла .pgpass:
#хост:порт:база:пользователь:пароль
#в нашем случае:
#localhost:5432:dolero-base:dolero-user:PASS_word
touch ~/.pgpass
chmod 600 ~/.pgpass
nano ~/.pgpass
----End create----

----Connect and backup database----
psql -h localhost -U dolero-user -d dolero-base
pg_dump -x -O -h localhost -U dolero-user -d dolero-base
pg_dump -x -O -h localhost -U dolero-user -d dolero-base -s > ~/database/DDL.sql
pg_dump -x -O -h localhost -U dolero-user -d dolero-base -a > ~/database/DUMP.sql
----End connect and backup database

psql -h localhost -U dolero-user -d dolero-base -f DDL.sql -- For create tables from file DDL.sql

