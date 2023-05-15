1. Controllare quanti iscritti ci sono stati ogni anno.
    - SHOW DATABASES;
    - USE `university_db`;
    - SELECT COUNT(*) AS `total students`, YEAR (`enrolment_date`) AS `year of enrolment`
        -> FROM `students`
        -> GROUP BY `year of enrolment`

2. Contare gli insegnanti che hanno l'ufficio nello stesso edificio
    - SELECT COUNT(*) AS `total teachers`, office_address
        -> FROM teachers
        -> GROUP BY office_address

3. Calcolare la media dei voti di ogni appello d'esame
    - SELECT AVG(`vote`) AS `average_vote`
        ->FROM `exam_student`
        ->GROUP BY `exam_id`;

4. Contare quanti corsi di laurea ci sono per ogni dipartimento
    -   SELECT COUNT(*) AS `departments`, `departments`.`name` AS `departments_name` 
        FROM `degrees` 
        JOIN `departments` ON `degrees`.`department_id` = `departments`.`id` 
        GROUP BY `degrees`.`department_id`
