2.1
    SELECT * FROM "bolcher"
2.2
    SELECT * FROM "bolcher" WHERE "bolcher_farve" = "Rød"
2.3
    SELECT * FROM "bolcher" WHERE "bolcher_farve" IN ("Rød", "Blå")
2.4
    SELECT * FROM "bolcher" WHERE "bolcher_farve" NOT IN ("Rød") ORDER BY "bolcher_navn" ASC
2.5
    SELECT * FROM "bolcher" WHERE "bolcher_navn" LIKE "B%"
2.6
    SELECT * FROM "bolcher" WHERE "bolcher_navn" LIKE "&e%"
2.7
    SELECT "bolcher_navn", "bolcher_vaegt" FROM "bolcher" WHERE "bolcher_vaegt" < 10 ORDER BY "bolcher_vaegt" ASC
2.8
    SELECT "bolcher_navn", "bolcher_vaegt" FROM "bolcher" WHERE "bolcher_vaegt" BETWEEN 10 AND 12 ORDER BY "bolcher_navn" ASC
2.9
    SELECT * FROM "bolcher" WHERE "bolcher_vaegt" ORDER BY "bolcher_vaegt" DESC LIMIT 3
2.10
    SELECT * FROM "bolcher" WHERE "bolcher_id" = FLOOR (RAND()*(8-1+1)+1)