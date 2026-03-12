1. Contare quanti iscritti ci sono stati ogni anno

SELECT enrolment_date, COUNT(\*) AS number_of_members
FROM university.students
GROUP BY enrolment_date

2. Contare gli insegnanti che hanno l'ufficio nello stesso edificio

SELECT office_address, COUNT(\*) AS same_address
FROM university.teachers
GROUP BY office_address

3. Calcolare la media dei voti di ogni appello d'esame

SELECT exam_id, AVG(vote) AS average_grades
FROM university.exam_student
GROUP BY exam_id

4. Contare quanti corsi di laurea ci sono per ogni dipartimento

SELECT department_id, COUNT(\*) AS degree_courses
FROM university.degrees
GROUP BY department_id
