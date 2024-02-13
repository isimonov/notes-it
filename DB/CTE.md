CTE (Common Table Expressions) - обобщённые табличные выражения

```sql
WITH t as (
    SELECT generate_series(1,3)
)
SELECT * FROM t;
```
# Recursive CTE

```sql
WITH RECURSIVE r AS (
    -- Anchor member
    SELECT 
        1 AS i, 
        1 AS factorial
    
    UNION
    
    -- Recursive member
    SELECT 
        i+1 AS i, 
        factorial * (i+1) as factorial 
    FROM r
    WHERE i < 10
)
SELECT * FROM r;
```

```sql
CREATE TABLE geo (
    id int4 NOT NULL,
    parent_id int4 NULL,
    "name" varchar(1000) NULL,
    CONSTRAINT geo_pkey PRIMARY KEY (id),
    CONSTRAINT geo_parent_id_fkey FOREIGN KEY (parent_id) REFERENCES geo(id)
);

INSERT INTO geo (id,parent_id,"name") VALUES
    (1,NULL,'Планета Земля'),
    (2,1,'Континент Евразия'),
    (3,1,'Континент Северная Америка'),
    (4,2,'Европа'),
    (5,4,'Россия'),
    (6,4,'Германия'),
    (7,5,'Москва'),
    (8,5,'Санкт-Петербург'),
    (9,6,'Берлин'),
    (10,7,'Мытищи'),
    (11,8,'Весёлый Посёлок'),
    (12,11,'ул. Тельмана');

WITH RECURSIVE r AS (
   SELECT id, parent_id, "name", 1 AS "level", '' AS "path"
   FROM geo
   WHERE id = 4

   UNION ALL

   SELECT geo.id, geo.parent_id, geo.name, r."level" + 1 AS "level", concat(path, ' / ', geo.name) AS "path"
   FROM geo
      JOIN r
          ON geo.parent_id = r.id
)
SELECT * FROM r WHERE "level" > 0 ORDER BY "path";
```
