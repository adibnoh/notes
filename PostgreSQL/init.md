# Init

## Create table with column

```sql

# Syntax
CREATE TABLE public.<table_name>
(
    <column_name> <column_type> <extra_parameter>,
    <additional_constraint>
)

# Sample
CREATE TABLE public.tb_location
(
    rec_id integer NOT NULL,
    parent_id integer NOT NULL,
    loc_name_id integer NOT NULL,
    PRIMARY KEY (rec_id)
)

```

## Add / Drop Foreign Key

```sql

# Syntax
alter table public.<table_name>
add constraint <constraint_name>
foreign key (foreign_key_column_name_inside_current_table)
references public.<reference_table>(<column_name_in_reference_table>)

# Sample
alter table public.tb_location
add constraint fk_location_loc_name_id
foreign key (loc_name_id)
references public.tb_loc_name(rec_id)

```