Query con Group by

1.  Contare quanti iscritti ci sono stati ogni anno

    SELECT
    COUNT(id)
    AS `total_students_signedup`, YEAR(`enrolment_date`) AS `year_signedup`
    FROM `students`
    GROUP BY `year_signedup`;

2.  Contare gli insegnanti che hanno l'ufficio nello stesso edificio

    SELECT
    COUNT(id)
    AS `total_teachers`, `office_address` AS `total_same_office`
    FROM `teachers`
    GROUP BY `total_same_office`;

3.  Calcolare la media dei voti di ogni appello d'esame

    SELECT `exam_id`,
    AVG(`vote`)
    AS `average_votes`
    FROM `exam_student`
    GROUP BY `exam_id`;

4.  Contare quanti corsi di laurea ci sono per ogni dipartimento

    SELECT `department_id`,
    COUNT(`name`) AS `total_courses`
    FROM `degrees`
    GROUP BY `department_id`;

Query con Join

1. Selezionare tutti gli studenti iscritti al Corso di Laurea in Economia

   SELECT `students`.`name` AS `student_name`, `students`.`surname` AS `student_surname`, `students`.`date_of_birth` AS `student_date_of_birth`, `students`.`fiscal_code` AS `student_fiscal_code`, `students`.`enrolment_date` AS `student_enrolment_data`, `students`.`registration_number` AS `student_registration_number`, `students`.`email` AS `student_email`
   FROM `students`
   JOIN `degrees` ON `degrees`.`id` = `students`.`degree_id`
   WHERE `degrees`.`name` = 'Corso di Laurea in Economia';

2. Selezionare tutti i Corsi di Laurea del Dipartimento di Neuroscienze

   SELECT `degrees`.`name` AS `name_degree`, `degrees`.`level` AS `level_degree`, `degrees`.`address` AS `address_degree`, `degrees`.`email` AS `email_degree`, `degrees`.`website` AS `website_degree`
   FROM `degrees`
   JOIN `departments` ON `departments`.`id` = `degrees`.`department_id`
   WHERE `departments`.`name` = 'Dipartimento di Neuroscienze';

3. Selezionare tutti i corsi in cui insegna Fulvio Amato (id=44)

   SELECT `courses`.`name` AS `name_course`, `courses`.`description` AS `description_course`, `courses`.`period` AS `period_course`, `courses`.`year` AS `year_course`, `courses`.`cfu` AS `cfu_course`, `courses`.`website` AS `website_course`
   FROM `courses`
   JOIN `course_teacher` ON `courses`.`id` = `course_teacher`.`course_id`
   WHERE `teacher_id` = 44

4. Selezionare tutti gli studenti con i dati relativi al corso di laurea a cui sono iscritti e il relativo dipartimento, in ordine alfabetico per cognome e nome
5. Selezionare tutti i corsi di laurea con i relativi corsi e insegnanti
6. Selezionare tutti i docenti che insegnano nel Dipartimento di Matematica (54)

BONUS: Selezionare per ogni studente quanti tentativi d’esame ha sostenuto per superare ciascuno dei suoi esami
