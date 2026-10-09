# Bài thực hành: Hàm & GROUP BY trong MySQL

## 📋 Thông tin
- **Database:** QuanLySinhVien
- **Công cụ:** MySQL Workbench
- **Số lượng truy vấn:** 4

## 📝 Danh sách các truy vấn

### Truy vấn 1: Số lượng sinh viên theo nơi ở
```sql
SELECT Address, COUNT(StudentId) AS 'Số lượng học viên'
FROM Student
GROUP BY Address;
Truy vấn 2: Điểm TB của mỗi học viên
sql
SELECT S.StudentId, S.StudentName, AVG(Mark) AS 'Điểm trung bình'
FROM Student S 
JOIN Mark M ON S.StudentId = M.StudentId
GROUP BY S.StudentId, S.StudentName;
Truy vấn 3: Học viên có điểm TB > 15
sql
SELECT S.StudentId, S.StudentName, AVG(Mark) AS 'Điểm trung bình'
FROM Student S 
JOIN Mark M ON S.StudentId = M.StudentId
GROUP BY S.StudentId, S.StudentName
HAVING AVG(Mark) > 15;
Truy vấn 4: Học viên có điểm TB lớn nhất
sql
SELECT S.StudentId, S.StudentName, AVG(Mark) AS 'Điểm trung bình'
FROM Student S 
JOIN Mark M ON S.StudentId = M.StudentId
GROUP BY S.StudentId, S.StudentName
HAVING AVG(Mark) >= ALL (
    SELECT AVG(Mark) 
    FROM Mark 
    GROUP BY Mark.StudentId
);