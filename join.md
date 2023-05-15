1. Selezionare tutti gli studenti iscritti al Corso di Laurea in Economia
    -   SELECT `students`.`name`, `students`.`surname`, `students`.`registration_number` 
        FROM `students` 
        JOIN `degrees` ON `students`.`degree_id` = `degrees`.`id` 
        WHERE `degrees`.`name` = 'Corso di Laurea in Economia';

2. Selezionare tutti i Corsi di Laurea Magistrale del Dipartimento di Neuroscienze
    -   SELECT `degrees`.`name` as `degree_name`, `departments`.`name` as `department_name`
        FROM `degrees` 
        JOIN `courses` ON `courses`.`id` = `courses`.`degree_id` 
        JOIN `departments` ON `departments`.`id` = `degrees`.`department_id`
        WHERE `departments`.`name` = 'Dipartimento di Neuroscienze'
        AND `degrees`.`level` = 'magistrale'

3. Selezionare tutti i corsi in cui insegna Fulvio Amato (id=44)
    -   SELECT `teachers`.`name` as `teacher_name`, `teachers`.`surname` as `teacher_surname`, `courses`.`name` as `course_name`
        FROM `course_teacher`
        JOIN `teachers`ON `teachers`.`id` = `course_teacher`.`teacher_id` 
        JOIN `courses` ON `course_teacher`.`course_id`= `courses`.`id`
        WHERE `teachers`.`name` = 'Fulvio'
        AND `teachers`.`surname` = 'Amato'
        AND `teachers`.`id`= 44

4. Selezionare tutti gli studenti con i dati relativi al corso di laurea a cui sono iscritti e il relativo dipartimento, in ordine alfabetico per cognome e nome
    - SELECT `students`.`name` as `student_name`, `students`.`surname` as `student_surname`, `departments`.    `name` as `department_name`, `courses`.`name` as `course_name`
    FROM `students` 
    JOIN `degrees` ON `degrees`.`id` = `students`.`degree_id`
    JOIN `courses` ON `courses`.`degree_id` = `students`.`degree_id`
    JOIN `departments` ON `departments`.`id` = `degrees`.`department_id`
    ORDER BY `student_surname`, `student_name`;

5. Selezionare tutti i corsi di Laurea con i relativi corsi e insegnanti
    - SELECT `degrees`.`name` AS `degree_name`, `courses`.`name` AS `course_name`,`teachers`.`name`  AS `teacher_name`,`teachers`.`surname`  AS `teacher_surname`
    FROM `courses`
    JOIN `degrees`ON `degrees`.`id`= `courses`.`degree_id`
    JOIN `course_teacher`ON `course_teacher`.`course_id`= `courses`.`id`
    JOIN `teachers`ON `teachers`.`id`= `teachers`.`id`

6. Selezionare tutti i docenti che insegnano nel Dipartimento di Matematica (54)
    -SELECT DISTINCT `departments`.`name` AS `department_name`, `teachers`.`name` AS `teacher_name`, `teachers`.`surname` AS `teacher_surname`
    FROM `course_teacher`
    JOIN `teachers` ON `teachers`.`id` = `course_teacher`.`teacher_id`
    JOIN `courses` ON `courses`.`id` = `course_teacher`.`course_id`
    JOIN `degrees` ON `degrees`.`id` = `courses`.`degree_id` 
    JOIN `departments` ON `departments`.`id` = `degrees`.`department_id`
    WHERE `departments`.`name` = 'Dipartimento di Matematica';

7. BONUS. Selezionare per ogni studente quanti tentativi d'esame ha sostenuto per superare ciascuno dei suoi esami
    -SELECT `students`.`name` AS `student_name`, `students`.`surname` as `student_surname`, `courses`.`name` AS `course_name`, COUNT(`students`.`name`) AS `exam_attempts`  
    FROM `exam_student`
    JOIN `exams` ON `exam_student`.`exam_id` = `exams`.`id` 
    JOIN `students` ON `exam_student`.`student_id` = `students`.`id`
    JOIN `courses` ON `exams`.`course_id` = `courses`.`id` 
    GROUP BY `student_name`, `course_name`, `student_surname`
