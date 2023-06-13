SELECT *
FROM SleepHealth

--Average age of all people
SELECT AVG(Age) AS AverageAge 
FROM SleepHealth

--Number of people within each BMICategory
SELECT BMI_Category, COUNT(*) AS Count 
FROM SleepHealth 
GROUP BY BMI_Category
ORDER BY 2

--People with sleeping disorders
SELECT *
FROM SleepHealth
WHERE Sleep_Disorder != 'None'

-- Number of males with sleeping disorder vs females 
SELECT Gender, COUNT(Gender) AS DisorderCount
FROM SleepHealth
WHERE Sleep_Disorder != 'None'
GROUP BY Gender

--Average daily steps for each occupation
SELECT Occupation, AVG(Daily_Steps) AS Average_daily_steps
FROM SleepHealth
GROUP BY Occupation

--Number of people within an occupation who reported a stress level greater than or equal to 8
SELECT Occupation, COUNT(Occupation) AS OccupationCount
FROM SleepHealth
WHERE Stress_Level >= 8
GROUP BY Occupation
HAVING COUNT(Occupation) > 1

--Top 5 occupations with the highest average sleep duration
SELECT TOP 5 Occupation, AVG(Sleep_Duration) AS AvgSleepDuration
FROM SleepHealth
GROUP BY Occupation
ORDER BY AvgSleepDuration DESC

--Average heart rate for each BMI category
SELECT BMI_Category, AVG(Heart_Rate) AS AVGHeartRate
FROM SleepHealth
GROUP BY BMI_Category
ORDER BY 2

--Average sleep duration and quality of sleep for different occupations
SELECT Occupation, AVG(sleep_duration) AS AvgSleepDuration, AVG(quality_of_sleep) AS AvgQualityOfSleep
FROM SleepHealth
GROUP BY Occupation
ORDER BY 2 DESC, 3 DESC

-- Comparison of average physical activity levels and stress levels for people with a sleeping disorder vs without
SELECT AVG(physical_activity_level) AS AvgPhysicalActivityLevel , AVG(stress_level) AS AvgStressLevel
FROM SleepHealth
WHERE Sleep_Disorder != 'None'

SELECT AVG(physical_activity_level) AS AvgPhysicalActivityLevel , AVG(stress_level) AS AvgStressLevel
FROM SleepHealth
WHERE Sleep_Disorder = 'None'

SELECT *,
  CASE
    WHEN Age < 18 THEN 'Under 18'
    WHEN Age BETWEEN 18 AND 30 THEN '18-30'
    WHEN Age BETWEEN 31 AND 45 THEN '31-45'
    WHEN Age BETWEEN 46 AND 60 THEN '46-60'
    ELSE 'Over 60'
  END AS AgeGroup
FROM SleepHealth

--Average sleep duration and quality of sleep for different age ranges
SELECT AVG(Sleep_duration) AS AvgSleepDuration, AVG(Quality_of_Sleep) AvgQualityOfSleep
FROM SleepHealth
WHERE Age BETWEEN 18 AND 30
 
SELECT AVG(Sleep_duration) AS AvgSleepDuration, AVG(Quality_of_Sleep) AvgQualityOfSleep
FROM SleepHealth
WHERE Age BETWEEN 31 AND 45

SELECT AVG(Sleep_duration) AS AvgSleepDuration, AVG(Quality_of_Sleep) AvgQualityOfSleep
FROM SleepHealth
WHERE Age BETWEEN 46 AND 60

--Occupations having a max heart rate greater than 80 bpm
SELECT Occupation, MAX(Heart_Rate) AS MaxHeartRate
FROM SleepHealth
GROUP BY Occupation
HAVING MAX(Heart_Rate) > 80

--Number of obese and overwight people within each occupation
SELECT Occupation, COUNT(BMI_Category) AS ObeseAndOverweightCount
FROM SleepHealth
WHERE BMI_Category in ('Obese', 'Overweight')
GROUP BY Occupation
ORDER BY ObeseAndOverweightCount

--Total number of people with sleeping disorders within each occupation
SELECT Gender, Age, Occupation, COUNT(Sleep_Disorder) OVER (PARTITION BY Occupation) AS SleepDisorderCount
FROM SleepHealth
WHERE Sleep_Disorder <> 'None'
