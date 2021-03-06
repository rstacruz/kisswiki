```sql
INSERT into foo_bar (foo_id, bar_id) VALUES ((select id from foo where name = 'selena'), (select id from bar where type = 'name'));
```

http://www.chesnok.com/daily/2013/11/19/everyday-postgres-insert-with-select/comment-page-1/

## always lowercase

```sql
CREATE TABLE foobar (
    foo text,
    bar int
);

CREATE OR REPLACE FUNCTION lowecase_foo_on_insert() RETURNS trigger AS $lowecase_foo_on_insert$
    BEGIN        
        NEW.foo = LOWER(NEW.foo);
        RETURN NEW;
    END;
$lowecase_foo_on_insert$ LANGUAGE plpgsql;

CREATE TRIGGER lowecase_foo_on_insert_trigger BEFORE INSERT OR UPDATE ON foobar
    FOR EACH ROW EXECUTE PROCEDURE lowecase_foo_on_insert();

INSERT INTO foobar (foo, bar) VALUES ('LOWERCASE ME', 1);
SELECT * FROM foobar;
```

http://stackoverflow.com/questions/18807709/create-a-postgres-rule-or-trigger-to-automatically-convert-a-column-to-lowercase/18939742#18939742

## insert on conflict do update


```sql
INSERT INTO the_table (id, column_1, column_2) 
VALUES (1, 'A', 'X'), (2, 'B', 'Y'), (3, 'C', 'Z')
ON CONFLICT (id) DO UPDATE 
  SET column_1 = excluded.column_1, 
      column_2 = excluded.column_2;
```

http://stackoverflow.com/questions/1109061/insert-on-duplicate-update-in-postgresql
