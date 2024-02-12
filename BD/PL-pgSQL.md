# Foreach loop array 

```SQL
DO
$do$
DECLARE
   _arr  int[] := '{1,2,3,4,5,6,7,8,9}';
   _elem int;              
BEGIN
   FOREACH _elem IN ARRAY _arr
   LOOP 
      INSERT INTO test (id, test_id) VALUES (1, _elem);
   END LOOP;
END
$do$;
```