# DatabaseDataset
SOCIAL MEDIA USERS'.

-- # Data dive;. 
Difficulties:
The dataset available is inconsistency and lack normalization of any kind.It also has dublicate values such as Jacquelin Cook has 'Fashion' listed twice.
The data entry can lead to wrong analysis due to its data entry errors.
--# 2 DATA FUN .
Sql querry
--select *from Users

.Use basic SQL queries like (COUNT, AVG, and SUM) to understand more about the data you have
--SELECT Gender, COUNT(*) as Count
FROM Users
GROUP BY Gender;

--SELECT AVG(YEAR(CURDATE()) - YEAR(DOB)) as AverageAge
FROM Users;

Total numbers of users.
--SELECT COUNT(*) as TotalUsers
FROM Users;

Total number of interests
--SELECT SUM(LENGTH(Interests) - LENGTH(REPLACE(Interests, ',', '')) + 1) as TotalInterests
FROM Users;
# Ask Away (30 pts)
#1-- First, create a temporary table to store individual interests
CREATE VAARIABLES TABLE UserInterests AS
SELECT UserID, Country, TRIM(SUBSTRING_INDEX(SUBSTRING_INDEX(Interests, ',', numbers.n), ',', -1)) as Interest
FROM (
    SELECT 1 as n UNION ALL SELECT 2 UNION ALL SELECT 3 UNION ALL SELECT 4
    UNION ALL SELECT 5 UNION ALL SELECT 6 UNION ALL SELECT 7 UNION ALL SELECT 8
    UNION ALL SELECT 9 UNION ALL SELECT 10
) numbers INNER JOIN Users
ON CHAR_LENGTH(Interests) - CHAR_LENGTH(REPLACE(Interests, ',', '')) >= numbers.n - 1;

-- Now, query the most common interests per country
SELECT Country, Interest, COUNT(*) as InterestCount
FROM UserInterests
GROUP BY Country, Interest
ORDER BY Country, InterestCount DESC;

#2.WHAT IS THE AVERAGE AGE OF USERS FROM EACH COUNTRY
-- Calculate the age and find the average per country
SELECT Country, AVG(YEAR(CURDATE()) - YEAR(DOB)) as AverageAge
FROM Users
GROUP BY Country;
#Write basic SQL queries (WHERE, ORDER BY) to find answers.
..WHERE
CREATE VARIABLES TABLE UserInterests AS
SELECT UserID, Country, TRIM(SUBSTRING_INDEX(SUBSTRING_INDEX(Interests, ',', numbers.n), ',', -1)) as Interest
FROM (
    SELECT 1 as n UNION ALL SELECT 2 UNION ALL SELECT 3 UNION ALL SELECT 4
    UNION ALL SELECT 5 UNION ALL SELECT 6 UNION ALL SELECT 7 UNION ALL SELECT 8
    UNION ALL SELECT 9 UNION ALL SELECT 10
) numbers INNER JOIN Users
ON CHAR_LENGTH(Interests) - CHAR_LENGTH(REPLACE(Interests, ',', '')) >= numbers.n - 1;

--FIND ALL USERS FROM SPECIFIC COUNTRIES
SELECT * 
FROM Users 
WHERE Country = 'India';
--ORDER BY
fIND THE YOUNGEST USER
SELECT * 
FROM Users 
ORDER BY DOB DESC 
LIMIT 5; -- Limiting to top 5 youngest users





