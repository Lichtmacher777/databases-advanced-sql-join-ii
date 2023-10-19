# Start

## task 1

<pre>student_mentor=# SELECT
    s.name AS &quot;Student&quot;,
    m.name AS &quot;Mentor&quot;,
    lm.name AS &quot;Local mentor&quot;
FROM
    student s
LEFT JOIN
    mentor m ON s.mentor_id = m.id
LEFT JOIN
    mentor lm ON s.local_mentor = lm.id
ORDER BY
    s.name;
      Student       |      Mentor      |  Local mentor   
--------------------+------------------+-----------------
 Aimaar Abdul       | Peter Smith      | Laura Wild
 Alex Anjou         | Julius Maxim     | Fabienne Martin
 Christian Blanc    | Melinda O&apos;Connor | Fabienne Martin
 Dolores Perez      | Laura Wild       | Julia Vila
 Emilio Ramiro      |                  | Julia Vila
 Gerald Hutticher   | Julia Vila       | Julius Maxim
 Gudrun Schmidt     | Patricia Boulard | Julius Maxim
 Irmgard Seekircher | Fabienne Martin  | Julius Maxim
 Itzi Elizabal      | Melinda O&apos;Connor | Julia Vila
 John Goldwin       | Julia Vila       | Laura Wild
 Maria Highsmith    | Julius Maxim     | Peter Smith
 Wayne Green        |                  | Peter Smith
(12 rows)

</pre>

## task 2

<pre>      Student       |         Topic          |      Mentor      
--------------------+------------------------+------------------
 Aimaar Abdul       | Python Algorithms      | Peter Smith
 Alex Anjou         | Advanced SQL           | Julius Maxim
 Christian Blanc    | Computer Basics        | Melinda O&apos;Connor
 Dolores Perez      | Django Basics          | Laura Wild
 Dolores Perez      | Frontend               | Laura Wild
 Dolores Perez      | Python Web Frameworks  | Laura Wild
 Emilio Ramiro      |                        | 
 Gerald Hutticher   | Python Data Structures | Julia Vila
 Gudrun Schmidt     | Python Basics          | Patricia Boulard
 Irmgard Seekircher | SQL                    | Fabienne Martin
 Itzi Elizabal      | Computer Basics        | Melinda O&apos;Connor
 John Goldwin       | Python Data Structures | Julia Vila
 Maria Highsmith    | Advanced SQL           | Julius Maxim
 Wayne Green        |                        | 
(14 rows)
</pre>

## task 3

<pre>student_mentor=# SELECT
    m.name AS &quot;Topic&quot;,
    COALESCE(mn.name, &apos;&apos;) AS &quot;Mentor&quot;,
    COALESCE(s.name, &apos;&apos;) AS &quot;Student&quot;
FROM
    module m
LEFT JOIN
    mentor mn ON m.teacher = mn.id
LEFT JOIN
    student s ON mn.id = s.local_mentor
ORDER BY
    m.name, mn.name, s.name;
         Topic          |      Mentor      |      Student       
------------------------+------------------+--------------------
 Advanced SQL           | Julius Maxim     | Gerald Hutticher
 Advanced SQL           | Julius Maxim     | Gudrun Schmidt
 Advanced SQL           | Julius Maxim     | Irmgard Seekircher
 Computer Basics        | Melinda O&apos;Connor | 
 Database Basics        | Ahmed Ali        | 
 Django Admin           | Rose Dupond      | 
 Django Basics          | Laura Wild       | Aimaar Abdul
 Django Basics          | Laura Wild       | John Goldwin
 Django ORM             |                  | 
 Frontend               | Laura Wild       | Aimaar Abdul
 Frontend               | Laura Wild       | John Goldwin
 Python Algorithms      | Peter Smith      | Maria Highsmith
 Python Algorithms      | Peter Smith      | Wayne Green
 Python Basics          | Patricia Boulard | 
 Python Data Structures | Julia Vila       | Dolores Perez
 Python Data Structures | Julia Vila       | Emilio Ramiro
 Python Data Structures | Julia Vila       | Itzi Elizabal
 Python Web Frameworks  | Laura Wild       | Aimaar Abdul
 Python Web Frameworks  | Laura Wild       | John Goldwin
 SQL                    | Fabienne Martin  | Alex Anjou
 SQL                    | Fabienne Martin  | Christian Blanc
(21 rows)
</pre>

## task 4

<pre>student_mentor=# SELECT
    m.name AS &quot;Topic&quot;,
    mentor.name AS &quot;Mentor&quot;,
    student.name AS &quot;Student&quot;
FROM
    module m
LEFT JOIN
    mentor ON m.teacher = mentor.id
LEFT JOIN
    student ON m.teacher = student.local_mentor OR m.teacher = student.mentor_id
WHERE
    mentor.city = &apos;Berlin&apos; OR student.city = &apos;Berlin&apos;
ORDER BY
    m.name, mentor.name, student.name;
         Topic          |      Mentor      |      Student       
------------------------+------------------+--------------------
 Advanced SQL           | Julius Maxim     | Alex Anjou
 Advanced SQL           | Julius Maxim     | Gerald Hutticher
 Advanced SQL           | Julius Maxim     | Gudrun Schmidt
 Advanced SQL           | Julius Maxim     | Irmgard Seekircher
 Advanced SQL           | Julius Maxim     | Maria Highsmith
 Computer Basics        | Melinda O&apos;Connor | Christian Blanc
 Computer Basics        | Melinda O&apos;Connor | Itzi Elizabal
 Python Basics          | Patricia Boulard | Gudrun Schmidt
 Python Data Structures | Julia Vila       | Gerald Hutticher
 SQL                    | Fabienne Martin  | Irmgard Seekircher
(10 rows)
</pre>

# Finish
