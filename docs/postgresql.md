


## Install PostGreSQL 10
## Ubuntu 16.04
- Uninstall if any previous version
- Update & install
```
sudo apt-get update
sudo apt-get install postgresql postgresql-contrib
```

- Ensure that the server is started by switching to the postgres user.
```
sudo -u postgres psql
```
 
## Connect to a database
```
psql -d bses_pdm
```
## Check current database from PSQL prompt
```
\conninfo
```
## Change password
-
```
psql -U postgres
postgres=# alter user postgres with password 'NEW_PASSWORD';
postgresl=# \q
```
## Create table like another table
- With structure & data
```
CREATE TABLE target_table AS table source_table;
```
- With only structure
```
TABLE target_table AS table source_table with no data;
```
## Backup 
- 
```
/usr/bin/pg_dump --file "/home/user/db_name.bak" --host "xxx.xxx.xx.xx" --port "5432" --username ":username" ":dbname" -v
```
- [https://www.digitalocean.com/community/tutorials/how-to-backup-postgresql-databases-on-an-ubuntu-vps](https://www.digitalocean.com/community/tutorials/how-to-backup-postgresql-databases-on-an-ubuntu-vps)
## Python install
```
pip install psycopg2-binary
```

## SQLAlchemy connection strin
```
from sqlalchemy import create_engine
engine = create_engine('postgresql://scott:tiger@localhost:5432/mydatabase')
```

## Create UNIQUE Constraint

- We create a unique index
```
CREATE UNIQUE INDEX CONCURRENTLY candidate_skill_vector_candidate_detail_id 
ON candidate_skill_vector (candidate_detail_id);
```
- We add a unique constraint to the equipment table using the equipment_equip_id index
```
ALTER TABLE equipment 
ADD CONSTRAINT unique_equip_id 
UNIQUE USING INDEX equipment_equip_id;
```
- [http://www.postgresqltutorial.com/postgresql-unique-constraint/](http://www.postgresqltutorial.com/postgresql-unique-constraint/)

## Datetime with default UTC time
```
create table tablename(
id serial primary key,
filename varchar(500) not null,
item_list jsonb not null,
created_at timestamp with time zone default(now() at time zone 'UTC')
```
## Create FOREIGN Key constraint
```

Add field client to job

ALTER TABLE "jobs" ADD COLUMN "client_id" integer NULL;
CREATE INDEX "jobs_client_id_d72bc1fd" ON "jobs" ("client_id");
ALTER TABLE "jobs" ADD CONSTRAINT "jobs_client_id_d72bc1fd_fk_client_id" FOREIGN KEY ("client_id") REFERENCES "client" ("id") DEFERRABLE INITIALLY DEFERRED;
COMMIT;

```

## Create table
```
CREATE TABLE "jobs" ("id" serial NOT NULL PRIMARY KEY, "gmailid" varchar(1000) NULL, "req_jobid" varchar(1000) NULL, "job_title" varchar(1000) NULL, "city" varchar(1000) NULL, "zipcode" varchar(1000) NULL, "type_of_opening" varchar(1000) NULL, "client_contact_designation" varchar(1000) NULL, "degree" jsonb NULL, "primary_skills" jsonb NULL, "secondary_skills" jsonb NULL, "work_hours" varchar(1000) NULL, "client_contact_phone" varchar(1000) NULL, "client_contact_email" varchar(1000) NULL, "work_auth" varchar(1000) NULL, "overtime" varchar(1000) NULL, "travel_req" varchar(1000) NULL, "num_openings" varchar(100) NULL, "billing_rate" varchar(100) NULL, "domains" jsonb NULL, "tools" jsonb NULL, "work_ex" varchar(1000) NULL, "jd_skills" jsonb NULL, "jd_skills_vector" jsonb NULL, "jd_content" text NULL, "created_at" timestamp with time zone NOT NULL, "updated_at" timestamp with time zone NULL, "client_id" integer NULL, "email_id" integer NULL);
```

## Alter table
```
ALTER TABLE "jobs" ADD CONSTRAINT "jobs_client_id_d72bc1fd_fk_client_id" FOREIGN KEY ("client_id") REFERENCES "client" ("id") DEFERRABLE INITIALLY DEFERRED;
ALTER TABLE "jobs" ADD CONSTRAINT "jobs_email_id_81a0d42b_fk_email_messages_id" FOREIGN KEY ("email_id") REFERENCES "email_messages" ("id") DEFERRABLE INITIALLY DEFERRED;
CREATE INDEX "jobs_client_id_d72bc1fd" ON "jobs" ("client_id");
CREATE INDEX "jobs_email_id_81a0d42b" ON "jobs" ("email_id");
COMMIT;
```


## Command prompt
- Get to Postgres prompt with user postgres
```
sudo -u postgres psql
```
- List databases
```
\l
SELECT datname from pg_database;
```
- Select database
```
\c dbname
```
- Show connection information
```
\conninfo
```
- View all tables (this command shows all tables, as well as tables named like 'tbl_id_seq' that is of type sequence. This is a representation of serial type in the table(s), which have them. This keep track of the next number in the sequence and is created automatically for columns of this type.)
```
\t
```
- View all tables (without sequence types)
```
\dt
```
- Kill a query process
Reference: [https://stackoverflow.com/questions/5108876/kill-a-postgresql-session-connection](https://stackoverflow.com/questions/5108876/kill-a-postgresql-session-connection)
```
SELECT * FROM pg_stat_activity;
SELECT 
pg_terminate_backend(pid) 
FROM 
pg_stat_activity 
WHERE 
-- don't kill my own connection!
pid <> pg_backend_pid()
-- don't kill the connections to other databases
AND datname = 'database_name'
;
```
Before executing this query, you have to REVOKE the CONNECT privileges to avoid new connections:
```
REVOKE CONNECT ON DATABASE dbname FROM PUBLIC, username;
```