Sprint 1 Design Document Template
Deployment Environment
Link to your deployment environment

Functional Requirements
Use Case Name A
Functional Requirement 1
Functional Requirement 2
... etc.
Use Case Name B
Functional Requirement 1
Functional Requirement 2
... etc.
... etc.
Database Design
ERD
ERD

DDL
    CREATE TABLE "contributor_affiliations" (
    "ght_cntrb_id" int4 NOT NULL,
    "ca_id" int4 NOT NULL,
    "ca_domain" varchar(64) NOT NULL,
    "ca_affiliation" varchar(64) NOT NULL,
    "ca_start_date" date NOT NULL DEFAULT '\'1970-01-01\'',
    "ca_active" int2 NOT NULL DEFAULT 1,
    "ca_last_modified" timestamp(0) NOT NULL DEFAULT 'current_timestamp(6)',
    PRIMARY KEY ("ca_id", "ght_cntrb_id") 
    )
    WITHOUT OIDS;
    CREATE UNIQUE INDEX "domain,affiliation,start_date" ON "contributor_affiliations" ("ca_domain" ASC, "ca_affiliation" ASC, "ca_start_date" ASC);
    CREATE INDEX "domain,active" ON "contributor_affiliations" ("ca_domain" ASC, "ca_active" ASC);

    CREATE TABLE "contributors_aliases" (
    "ght_cntrb_id" int4 NOT NULL,
    "cntrb_a_id" int4 NOT NULL,
    "cntrb_canonical" varchar(128) NOT NULL,
    "cntrb_alias" varchar(128) NOT NULL,
    "cntrb_active" int2 NOT NULL DEFAULT 1,
    "cntrb_last_modified" timestamp(0) NOT NULL DEFAULT 'current_timestamp(6)',
    PRIMARY KEY ("ght_cntrb_id", "cntrb_a_id") 
    )
    WITHOUT OIDS;
    CREATE UNIQUE INDEX "canonical,alias" ON "contributors_aliases" ("cntrb_canonical" ASC, "cntrb_alias" ASC);
    CREATE INDEX "alias,active" ON "contributors_aliases" ("cntrb_alias" ASC, "cntrb_active" ASC);
    COMMENT ON TABLE "contributors_aliases" IS 'An alias will need to be created for every contributor in this model, otherwise we will have to look in 2 places. ';

%% ETC
Files that are stubbed out in your repository, with comments about the use cases they are connected to. These sections may not all exist for the Zephyr project teams. Simply explain them as best you can.
User Interface Files
first one
second one
etc.
Model Files (Database Access)
first one
second one
etc
Controller Files (API or other)
first one
second one
etc.
Describe languages you need to use, and any gaps in skills on your team.
first language
how you will use examples or learn what you need
second language
how you will use examples or learn what you need
Skill gaps, if any, otherwise specify who is doing what
name
name
skill gap
