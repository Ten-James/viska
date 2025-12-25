> Saves an association as a table with foreign keys to the tables that are linked by the association.

```cs
public class Student
{
    public int Id { get; set; }
    public List<Course> Courses { get; set; }
}

public class StudentMapper
{
    public void SaveCourses(Student student)
    {
        // Nejdřív smaže staré vztahy
        var deleteSql = "DELETE FROM student_courses WHERE student_id = @studentId";
        ExecuteNonQuery(deleteSql, student.Id);

        // Pak přidá nové
        foreach (var course in student.Courses)
        {
            var insertSql = "INSERT INTO student_courses (student_id, course_id) VALUES (@studentId, @courseId)";
            ExecuteNonQuery(insertSql, student.Id, course.Id);
        }
    }

    public Student Find(int id)
    {
        var student = LoadStudent(id);

        // Načte vazby z asociační tabulky
        var sql = @"SELECT c.* FROM courses c
                    JOIN student_courses sc ON c.id = sc.course_id
                    WHERE sc.student_id = @studentId";
        student.Courses = LoadCourses(sql, id);

        return student;
    }
}
```

Pro many-to-many vztahy se používá samostatná asociační tabulka (např. student_courses), která obsahuje foreign keys na obě entity.

![[Pasted image 20251222101002.png]]

**Kombinuje se s:**
- [[Data mapper]] - implementuje mapování M:N relací
- [[Foreign key mapping]] - používá foreign keys
- [[Identity field]] - pro identifikaci objektů v asociaci

