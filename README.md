Welcome to your new dbt project!

``` sql
-- create accounts
use role accountadmin;

create warehouse dbt_wh with warehouse_size='x-small';
create database if not exists dbt_db;
create role if not exists dbt_role;

show grants on warehouse dbt_wh;

CREATE OR REPLACE USER gg
PASSWORD = ' '
DEFAULT_WAREHOUSE = dbt_wh
default_role = dbt_role
;


grant role dbt_role to user gg;


grant usage on warehouse dbt_wh to role dbt_role;
grant all on database dbt_db to role dbt_role;

use role dbt_role;

create schema if not exists dbt_db.dbt_schema;

grant role dbt_role to user gg;

grant usage on schema dbt_db.dbt_schema to role dbt_role;
GRANT ALL ON ALL TABLES IN SCHEMA dbt_db.dbt_schema  TO ROLE dbt_role; 
GRANT ALL ON ALL VIEWS IN SCHEMA dbt_db.dbt_schema  TO ROLE dbt_role; 


grant all on future tables in schema dbt_db.dbt_schema to role dbt_role;
grant all on future views in schema dbt_db.dbt_schema to role dbt_role;

grant create view on schema dbt_db.dbt_schema to role dbt_role;
grant create table on schema dbt_db.dbt_schema to role dbt_role;



grant role dbt_role to user gg; 


-- clean up
use role accountadmin;

drop warehouse if exists dbt_wh;
drop database if exists dbt_db;
drop role if exists dbt_role;


use role dbt_role;
use role ACCOUNTADMIN;


```
### Using the starter project

Try running the following commands:
- dbt run
- dbt test


### Resources:
- Learn more about dbt [in the docs](https://docs.getdbt.com/docs/introduction)
- Check out [Discourse](https://discourse.getdbt.com/) for commonly asked questions and answers
- Join the [chat](https://community.getdbt.com/) on Slack for live discussions and support
- Find [dbt events](https://events.getdbt.com) near you
- Check out [the blog](https://blog.getdbt.com/) for the latest news on dbt's development and best practices
# dbt-demo-sf
