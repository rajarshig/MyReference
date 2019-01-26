


## Install PostGreSQL 10
## Ubuntu 16.04
- Uninstall if any previous version
- Add the official postgres apt repository
```

Ubuntu 14.04: sudo add-apt-repository 'deb http://apt.postgresql.org/pub/repos/apt/ trusty-pgdg main'
Ubuntu 16.04: sudo add-apt-repository 'deb http://apt.postgresql.org/pub/repos/apt/ xenial-pgdg main'
Ubuntu 17.04: sudo add-apt-repository 'deb http://apt.postgresql.org/pub/repos/apt/ zesty-pgdg main'
```
- Import the repository signing key, followed by an update to the package lists
```
wget --quiet -O - https://www.postgresql.org/media/keys/ACCC4CF8.asc | \
  sudo apt-key add -
sudo apt-get update
```
- Install 
```
sudo apt-get install postgres-10
```
- Ensure that the server is started by switching to the postgres user.
```
sudo su - postgresql
```
 ## Python install
 ```
 pip install psycopg2-binary
 ```

 ## SQLAlchemy connection string
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
ALTER TABLE "jobs" ADD CONSTRAINT "jobs_client_id_d72bc1fd_fk_client_id" FOREIGN KEY ("client_id") REFERENCES "client" ("id") DEFERRABLE INITIALLY DEFERRED;
ALTER TABLE "jobs" ADD CONSTRAINT "jobs_email_id_81a0d42b_fk_email_messages_id" FOREIGN KEY ("email_id") REFERENCES "email_messages" ("id") DEFERRABLE INITIALLY DEFERRED;
CREATE INDEX "jobs_client_id_d72bc1fd" ON "jobs" ("client_id");
CREATE INDEX "jobs_email_id_81a0d42b" ON "jobs" ("email_id");
COMMIT;
```