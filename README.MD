1. Selezionare tutti gli studenti nati nel 1990 (160)
    - SHOW DATABASES;
    - USE `university_db`;
    - SHOW TABLES;
    - DESCRIBE `students`;
    -  SELECT *
        -> FROM `students`
        -> WHERE YEAR (`date_of_birth`)=1990;

2. Selezionare tutti i corsi che valgono più di 10 crediti (479)
    - SHOW DATABASES;
    - USE `university_db`;
    - SHOW TABLES;
    - DESCRIBE `courses`; 
    -  SELECT *
        -> FROM `courses`
        -> WHERE `cfu` > 10; 

3. Selezionare tutti gli studenti che hanno più di 30 anni
    - SHOW DATABASES;
    - USE `university_db`;
    - SHOW TABLES;
    - DESCRIBE `students`; 
    - SELECT *
        -> FROM `students`
        -> WHERE 2023 - YEAR (`date_of_birth`) > 30;

    [3501]

4. Selezionare tutti i corsi del primo semestre del primo anno di un qualsiasi corso di
laurea (286)
    - SHOW DATABASES;
    - USE `university_db`;
    - SHOW TABLES;
    - DESCRIBE `courses`; 
    - SELECT *
        -> FROM `courses` 
        -> WHERE `period`= "I semestre" AND YEAR = "1";

5. Selezionare tutti gli appelli d'esame che avvengono nel pomeriggio (dopo le 14) del
20/06/2020 (21)
    - SHOW DATABASES;
    - USE `university_db`;
    - SHOW TABLES;
    - DESCRIBE `exams`; 
    - SELECT *
        -> FROM `exams`
        -> WHERE `date`="2020-06-20" AND `hour`>="14:00:00";

6. Selezionare tutti i corsi di laurea magistrale (38)
   - SHOW DATABASES;
    - USE `university_db`;
    - SHOW TABLES;
    - DESCRIBE `degrees`;
    - SELECT *
        -> FROM `degrees`
        -> WHERE `level` = "magistrale";

7. Da quanti dipartimenti è composta l'università? (12)
   - SHOW DATABASES;
    - USE `university_db`;
    - SHOW TABLES;
    - DESCRIBE `departments`;
    - SELECT COUNT(*) AS `total departments`
        -> FROM `departments`;

8. Quanti sono gli insegnanti che non hanno un numero di telefono? (50)
    - SHOW DATABASES;
    - USE `university_db`;
    - SHOW TABLES;
    - DESCRIBE `teachers;
    - SELECT *
        -> FROM `teachers`
        -> WHERE `phone` IS NULL