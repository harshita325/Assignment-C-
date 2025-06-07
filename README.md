# Assignment-C-
SELECT
    Start_Date,
    End_Date,
    Task_ID
FROM
    Projects
WHERE
    (End_Date - Start_Date) = INTERVAL '1' DAY -- This confirms the completion days are always 1
GROUP BY
    Start_Date, End_Date, Task_ID -- Group by all to ensure uniqueness, though Task_ID itself is unique
HAVING
    COUNT(*) > 0 -- This condition is always true since each row is a project. The real intent is to find if there are multiple projects that *collectively* share the same start and end dates.
ORDER BY
    Start_Date;
