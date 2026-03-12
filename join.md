1. Selezionare tutti gli studenti iscritti al Corso di Laurea in Economia

SELECT students.name,degrees.name AS enrolled_in_economic
FROM university.students
JOIN university.degrees
ON students.degree_id=degrees.id
WHERE degrees.name= '%Economia%'

2. Selezionare tutti i Corsi di Laurea Magistrale del Dipartimento di
   Neuroscienze

SELECT degrees.name AS magistral_courses
FROM university.degrees
JOIN university.departments
ON degrees.department_id = departments.id
WHERE degrees.name LIKE '%Magistrale%'
AND departments.name LIKE '%Neuroscienze%'

3. Selezionare tutti i corsi in cui insegna Fulvio Amato (id=44)

SELECT courses.id, courses.name
FROM courses
JOIN course_teacher
ON courses.id = course_teacher.course_id
WHERE course_teacher.teacher_id = 44

4. Selezionare tutti gli studenti con i dati relativi al corso di laurea a cui
   sono iscritti e il relativo dipartimento, in ordine alfabetico per cognome e
   nome

SELECT students.name, students.surname, degrees.name AS degree_name, departments.name AS department_name
FROM students
JOIN degrees
ON students.degree_id = degrees.id
JOIN departments
ON degrees.department_id = departments.id
ORDER BY students.name, students.surname

5. Selezionare tutti i corsi di laurea con i relativi corsi e insegnanti

SELECT degrees.name AS degree_name,
courses.name AS course_name,
teachers.name AS teacher_name,
teachers.surname AS teacher_surname
FROM degrees
JOIN courses
ON courses.degree_id = degrees.id
JOIN course_teacher
ON course_teacher.course_id = courses.id
JOIN teachers
ON course_teacher.teacher_id = teachers.id
ORDER BY degrees.name, courses.name, teachers.name, teachers.surname

6. Selezionare tutti i docenti che insegnano nel Dipartimento di
   Matematica (54)

SELECT teachers.name, teachers.surname,
degrees.name AS degree_name,
courses.name AS course_name,
departments.name AS department_name
FROM teachers
JOIN course_teacher
ON teachers.id = course_teacher.teacher_id
JOIN courses
ON course_teacher.course_id = courses.id
JOIN degrees
ON courses.degree_id = degrees.id
JOIN departments
ON degrees.department_id = departments.id
WHERE departments.name LIKE '%Matematica%'
ORDER BY teachers.surname, teachers.name, courses.name

7. BONUS: Selezionare per ogni studente il numero di tentativi sostenuti
   per ogni esame, stampando anche il voto massimo. Successivamente,
   filtrare i tentativi con voto minimo 18.
