REMEMBER TO OPEN XAMPP AND PRESS START!!!!!

Øvelse 1

1.1 Opret en database kaldet birgers_bolcher med én tabel kaldet bolche

1.2 Tabellen skal indeholde de viste felter og data – du bestemmer både feltnavne og datatyper

-----------------------------------------------------------------------------------------------------------------
Øvelse 2

2.1 - Udskriv alle informationer om alle bolcher.
    SELECT * FROM `bolcher` 

2.2 - Find og udskriv navnene på alle de røde bolcher.
    SELECT * FROM `bolcher` 
    WHERE `bolche_farve` = "Rød"

2.3 - Find og udskriv navnene på alle de røde og de blå bolcher, i samme SQL udtræk.
    SELECT * FROM `bolcher` 
    WHERE `bolche_farve` IN ("Rød", "Blå")

2.4 - Find og udskriv navnene på alle bolcher, der ikke er røde, sorteret alfabetisk.
    SELECT * FROM `bolcher` 
    WHERE `bolche_farve` NOT IN ("Rød") ORDER BY `bolche_navn` ASC

2.5 - Find og udskriv navnene på alle bolcher som starter med et “B”.
    SELECT * FROM `bolcher` 
    WHERE `bolche_navn` LIKE "B%"

2.6 - Find og udskriv navene på alle bolcher, hvor der i navnet findes mindst ét “e”.
    SELECT * FROM `bolcher` 
    WHERE `bolche_navn` LIKE "&e%"

2.7 - Find og udskriv navn og vægt på alle bolcher der vejer mindre end 10 gram, sorter stigende efter vægt.
    SELECT `bolche_navn`, `bolche_vaegt` FROM `bolcher` 
    WHERE `bolche_vaegt` < 10 ORDER BY `bolche_vaegt` ASC

2.8 - Find og udskriv navne på alle bolcher, der vejer mellem 10 og 12 gram (begge tal inklusiv), sorteret alfabetisk og derefter vægt.
    SELECT `bolche_navn`, `bolche_vaegt` FROM `bolcher` 
    WHERE `bolche_vaegt` BETWEEN 10 AND 12 ORDER BY `bolche_navn` ASC

2.9 - Find og udskriv de tre største (tungeste) bolcher.
    SELECT * FROM `bolcher` 
    WHERE `bolche_vaegt` 
    ORDER BY `bolche_vaegt` DESC LIMIT 3

2.10 - Udskriv alle informationer om et tilfældigt bolche, udvalgt af systemet (sql).
    SELECT * FROM `bolcher` 
    WHERE `bolche_id` = FLOOR (RAND()*(8-1+1)+1)
    
-------------------------------------------------------------------------------------------------------------------------------------------

Øvelse 3

3.1 Normaliser tabellen Bolcher så der dannes ”domænetabeller” til de felter hvor flere bolcher ofte har samme værdi.
    har lavet 6 domænetabeller
        bolche_smags_styrke
        bolche_smags_surhed
        bolche_farve
        bolche_smags_type    
        bolche_vaegt
        bolche_raavarepris
    de eneste værdier jeg har i den originale tabel er navn og id

-------------------------------------------------------------------------------------------------------------------------------------------

Øvelse 4 - 4.1 Gentag øvelse 2, men nu med inner joins

2.1 - Udskriv alle informationer om alle bolcher.
    SELECT * FROM `bolcher` 
    INNER JOIN `bolche_smags_styrke` 
    ON bolcher.FK_bolche_smags_styrke_id = bolche_smags_styrke.bolche_smags_styrke_id 
    INNER JOIN `bolche_smags_surhed` 
    ON bolcher.FK_bolche_smags_surhed_id = bolche_smags_surhed.bolche_smags_surhed_id 
    INNER JOIN `bolche_farve` 
    ON bolcher.FK_bolche_farve_id = bolche_farve.bolche_farve_id 
    INNER JOIN `bolche_smags_type` 
    ON bolcher.FK_bolche_smags_type_id = bolche_smags_type.bolche_smags_type_id 
    INNER JOIN `bolche_vaegt`
    ON bolcher.FK_bolche_vaegt_id = bolche_vaegt.bolche_vaegt_id
    INNER JOIN `bolche_raavarepris`
    ON bolcher.FK_bolche_raavarepris_id = bolche_raavarepris.bolche_raavarepris_id 

2.2 - Find og udskriv navnene på alle de røde bolcher.
    SELECT * FROM `bolcher` 
    INNER JOIN `bolche_farve` 
    ON bolcher.FK_bolche_farve_id = bolche_farve.bolche_farve_id 
    WHERE bolche_farve.bolche_farve_beskrivelse = "Rød" 

2.3 - Find og udskriv navnene på alle de røde og de blå bolcher, i samme SQL udtræk.
    SELECT * FROM `bolcher` 
    INNER JOIN `bolche_farve` 
    ON bolcher.FK_bolche_farve_id = bolche_farve.bolche_farve_id  
    WHERE bolche_farve.bolche_farve_beskrivelse IN ("Rød", "Blå")

2.4 - Find og udskriv navnene på alle bolcher, der ikke er røde, sorteret alfabetisk.
    SELECT * FROM `bolcher` 
    INNER JOIN `bolche_farve` 
    ON bolcher.FK_bolche_farve_id = bolche_farve.bolche_farve_id 
    WHERE bolche_farve.bolche_farve_beskrivelse NOT IN ("Rød") 
    ORDER BY `bolche_navn` ASC 

2.5 - Find og udskriv navnene på alle bolcher som starter med et “B”.
    SELECT * FROM `bolcher`             
    WHERE `bolche_navn` LIKE "B%" 

2.6 - Find og udskriv navene på alle bolcher, hvor der i navnet findes mindst ét “e”.
    SELECT * FROM `bolcher`            
    WHERE `bolche_navn` LIKE "%e%" 

2.7 - Find og udskriv navn og vægt på alle bolcher der vejer mindre end 10 gram, sorter stigende efter vægt.
    SELECT * FROM `bolcher` 
    INNER JOIN `bolche_vaegt`
    ON bolcher.FK_bolche_vaegt_id = bolche_vaegt.bolche_vaegt_id            
    WHERE bolche_vaegt.bolche_vaegt_beskrivelse < 10 ORDER BY bolche_vaegt.bolche_vaegt_beskrivelse ASC 

2.8 - Find og udskriv navne på alle bolcher, der vejer mellem 10 og 12 gram (begge tal inklusiv), sorteret alfabetisk og derefter vægt.
    SELECT * FROM `bolcher` 
    INNER JOIN `bolche_vaegt`
    ON bolcher.FK_bolche_vaegt_id = bolche_vaegt.bolche_vaegt_id            
    WHERE bolche_vaegt.bolche_vaegt_beskrivelse BETWEEN 10 AND 12 ORDER BY `bolche_navn` ASC

2.9 - Find og udskriv de tre største (tungeste) bolcher.
    SELECT * FROM `bolcher` 
    INNER JOIN `bolche_vaegt`
    ON bolcher.FK_bolche_vaegt_id = bolche_vaegt.bolche_vaegt_id            
    WHERE bolche_vaegt.bolche_vaegt_beskrivelse 
    ORDER BY bolche_vaegt.bolche_vaegt_beskrivelse DESC LIMIT 3 

2.10 - Udskriv alle informationer om et tilfældigt bolche, udvalgt af systemet (sql).
    SELECT * FROM `bolcher` 
    WHERE bolcher.bolche_id = FLOOR (RAND()*(8-1+1)+1) LIMIT 1 
----------------------------------------------------------------------------------------------------------------------------------------

Øvelse 5 

Nettopris for et bolche er råvareprisen plus 250 % (begge uden moms)
moms er 25% 

5.1 Udskriv en prisliste med bolchenavn og kilopris henholdsvis med og uden moms
    SELECT `bolche_navn`, 
    ((1000 / bolche_vaegt.bolche_vaegt_beskrivelse) * (bolche_raavarepris.bolche_raavarepris_beskrivelse / 100) * 2.5) AS nettopris, 
    (((1000 / bolche_vaegt.bolche_vaegt_beskrivelse) * (bolche_raavarepris.bolche_raavarepris_beskrivelse / 100) * 2.5) * 1.25) AS  nettopris_med_moms 
    FROM `bolcher` 
    INNER JOIN `bolche_raavarepris` 
    ON bolcher.FK_bolche_raavarepris_id = bolche_raavarepris.bolche_raavarepris_id 
    INNER JOIN `bolche_vaegt` 
    ON bolcher.FK_bolche_vaegt_id = bolche_vaegt.bolche_vaegt_id 
    
-------------------------------------------------------------------------------------------------------------------------------------------

Øvelse 6

6.1 Løs opgave 2.3 ved brug af IN
    SELECT * FROM `bolcher` 
    INNER JOIN `bolche_farve` 
    ON bolcher.FK_bolche_farve_id = bolche_farve.bolche_farve_id 
    WHERE bolche_farve.bolche_farve_beskrivelse IN ("Rød", "Blå")
 
6.2 Løs opgave 2.4 ved brug af NOT IN
    SELECT * FROM `bolcher` 
    INNER JOIN `bolche_farve` 
    ON bolcher.FK_bolche_farve_id = bolche_farve.bolche_farve_id 
    WHERE bolche_farve.bolche_farve_beskrivelse NOT IN ("Rød") 
    ORDER BY `bolche_navn` ASC 

6.3 Udskriv hvor mange bolscher der vejer under 15 g.
    SELECT * FROM `bolcher` 
    INNER JOIN `bolche_vaegt` 
    ON bolcher.FK_bolche_vaegt_id = bolche_vaegt.bolche_vaegt_id 
    WHERE bolche_vaegt.bolche_vaegt_beskrivelse < 15 
    ORDER BY bolche_vaegt.bolche_vaegt_beskrivelse ASC 

6.4 Udskriv hvor mange forskellige forskellige bolcher der er i tabellen

6.5 Udskriv gennemsnitsprisen per bolche
    Udefra råvareprisen
    SELECT AVG(`bolche_raavarepris_beskrivelse`) 
    FROM bolcher 
    INNER JOIN `bolche_raavarepris` 
    ON bolcher.FK_bolche_raavarepris_id = bolche_raavarepris.bolche_raavarepris_id 

6.6 Udskriv navn og pris på det dyreste og billigste bolche

-------------------------------------------------------------------------------------------------------------------------------------------

https://www.youtube.com/watch?v=bA8ldDeu6Ac&list=PLxUCQ4UtCuFsdb0fMWkLuim5zTaqtosvI