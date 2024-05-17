1. Selezionare tutti gli studenti iscritti al Corso di Laurea in Economia
- SELECT `students`.`name`,`students`.`surname`,`degrees`.`name` FROM `students` INNER JOIN `degrees` ON `students`.`degree_id` = `degrees`.`id` WHERE `degrees`.`name` = 'Corso di Laurea in Economia';  

2. Selezionare tutti i Corsi di Laurea Magistrale del Dipartimento di Neuroscienze
- SELECT * FROM `departments` INNER JOIN `degrees` ON `departments`.`id` = `degrees`.`department_id` WHERE `departments`.`name` = 'Dipartimento di Neuroscienze' AND `degrees`.`level` = 'magistrale'; 

3. Selezionare tutti i corsi in cui insegna Fulvio Amato (id=44)
- SELECT * FROM `teachers` INNER JOIN `course_teacher` ON `teachers`.`id` = `course_teacher`.`teacher_id` INNER JOIN `courses` ON `course_teacher`.`course_id` = `courses`.`id` WHERE `teachers`.`id` = 44; 

4. Selezionare tutti gli studenti con i dati relativi al corso di laurea a cui sono iscritti e il relativo dipartimento, in ordine alfabetico per cognome e nome
-SELECT * FROM `students` INNER JOIN `degrees` ON `degrees`.`id` = `students`.`degree_id` INNER JOIN `departments` ON `departments`.`id` = `degrees`.`department_id` ORDER BY `students`.`surname`, `students`.`name`; 

5. Selezionare tutti i corsi di laurea con i relativi corsi e insegnanti
- SELECT * FROM `degrees` INNER JOIN `courses` ON `degrees`.`id` = `courses`.`degree_id` INNER JOIN `course_teacher` ON `course_teacher`.`course_id` = `courses`.`id` INNER JOIN `teachers` ON `course_teacher`.`teacher_id` = `teachers`.`id`; 

6. Selezionare tutti i docenti che insegnano nel Dipartimento di Matematica (54)
- SELECT DISTINCT `teachers`.`name`,`teachers`.`surname` FROM `departments` INNER JOIN `degrees` ON `departments`.`id` = `degrees`.`department_id` INNER JOIN `courses` ON `degrees`.`id` = `courses`.`degree_id` INNER JOIN `course_teacher` ON `courses`.`id` = `course_teacher`.`course_id` INNER JOIN `teachers` ON `course_teacher`.`teacher_id` = `teachers`.`id` WHERE `departments`.`name` = 'Dipartimento di Matematica'; 

7. BONUS: Selezionare per ogni studente il numero di tentativi sostenuti per ogni esame, stampando anche il voto massimo. Successivamente, filtrare i tentativi con voto minimo 18.
- SELECT `students`.`name`,`students`.`surname`, `courses`.`id`, COUNT(`exams`.`id`), MAX(`exam_student`.`vote`) AS `voto_più_alto` FROM `students` INNER JOIN `exam_student` ON `students`.`id` = `exam_student`.`student_id` INNER JOIN `exams` ON `exam_student`.`exam_id` = `exams`.`id` INNER JOIN `courses` ON `exams`.`course_id` = `courses`.`id` GROUP BY `students`.`id`, `courses`.`id` HAVING MAX(`exam_student`.`vote`) >= 18; 