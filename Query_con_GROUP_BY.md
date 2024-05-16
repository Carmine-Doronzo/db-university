1. Contare quanti iscritti ci sono stati ogni anno
- SELECT COUNT(`id`), YEAR(`enrolment_date`) FROM `students` GROUP BY YEAR(`enrolment_date`); 

2. Contare gli insegnanti che hanno l'ufficio nello stesso edificio
- SELECT COUNT(`id`),`office_address` FROM `teachers` GROUP BY `office_address`; 

3. Calcolare la media dei voti di ogni appello d'esame
- SELECT `exams`.`date`, AVG(`exam_student`.`vote`) FROM `exams` INNER JOIN `exam_student` ON `exams`.`id` = `exam_student`.`exam_id` GROUP BY `exams`.`date`

4. Contare quanti corsi di laurea ci sono per ogni dipartimento
-