# Part 1.
## 1.3
1. INSERT INTO team (name, headquarters) VALUES ('Avengers', 'Los Angeles');

ERROR:  duplicate key value violates unique constraint "team_name_key"
DETAIL:  Key (name)=(Avengers) already exists.

2. INSERT INTO hero (name, team_id) VALUES ('Ghost', 99);

ERROR:  insert or update on table "hero" violates foreign key constraint "hero_team_id_fkey"
DETAIL:  Key (team_id)=(99) is not present in table "team".

3. INSERT INTO hero (age) VALUES (30);

ERROR:  null value in column "name" of relation "hero" violates not-null constraint
DETAIL:  Failing row contains (6, null, 30, null).

4. DELETE FROM team WHERE id = 1;

ERROR:  update or delete on table "team" violates foreign key constraint "hero_team_id_fkey" on table "hero"
DETAIL:  Key (id)=(1) is still referenced from table "hero".

❓ Question 1. For each of the four statements, which constraint blocked it ( PRIMARY KEY , UNIQUE , NOT
NULL , FOREIGN KEY ) and why?

Answer: 1. UNIQUE, 2. FOREIGN KEY, 3. NOT NULL, 4. FOREIGN KEY

❓ Question 2. The relationship team → hero is one-to-many. Why is the foreign key on hero and not on
team ?
Answer: The foreign key is placed on hero because team -> hero is a one-to-many relationship. One team can have many heroes, while each hero belongs to at most one team.

❓ Question 3. Heroes can go on many missions and a mission has many heroes (many-to-many). Sketch
the tables you need (names, columns, PK, FK). Hint: you need a link table.
Answer:
- "Mission" table:
   id (PK)
   name

- "Hero_Mission" table:
   hero_id (PK, FK -> Hero.id)
   mission_id (PK, FK -> Mission.id)

The Hero_Mission table is the link table.

--------------------------------------

# Part 2.
## 2.3
❓ Question 4. Why read the URL from an environment variable instead of writing it in database.py ?
Give two reasons.
