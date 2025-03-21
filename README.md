# Write the SQL query to find the second highest salary
## __Create the employees table__

```Sql
CREATE TABLE employees (
    employee_id SERIAL PRIMARY KEY,
    name VARCHAR(100),
    department VARCHAR(50),
    salary DECIMAL(10, 2)
);

-- Insert records for three departments
INSERT INTO employees (name, department, salary) VALUES 
('John Doe', 'Engineering', 63000),
('Jane Smith', 'Engineering', 55000),
('Michael Johnson', 'Engineering', 64000),
('Emily Davis', 'Marketing', 58000),
('Chris Brown', 'Marketing', 56000),
('Emma Wilson', 'Marketing', 59000),
('Alex Lee', 'Sales', 58000),
('Sarah Adams', 'Sales', 58000),
('Ryan Clark', 'Sales', 61000); 
```






## Approach 1 
-Using LIMIT & OFFSET
```Sql 
SELECT * FROM employees 
ORDER BY salary DESC
LIMIT 1 OFFSET 1; 
```





## Approach 2 
-Window function dense_rank
```Sql
SELECT *
FROM
(	SELECT *,
	DENSE_RANK() OVER( ORDER BY salary DESC) drn	
	FROM employees
) as subquery
WHERE drn = 2 
```

## Approach 3 
-Using max() aggregate function 
```Sql
SELECT * FROM employees
where MAX(salary)<(
      SELECT MAX(salary) FROM employees
)
```


-- Approach 2
-- Window function dense_rank
```Sql
SELECT *
FROM
(	SELECT *,
	DENSE_RANK() OVER( ORDER BY salary DESC) drn	
	FROM employees
) as subquery
WHERE drn = 2 
```
-- Approach 2
-- Window function dense_rank
```Sql
SELECT *
FROM
(	SELECT *,
	DENSE_RANK() OVER( ORDER BY salary DESC) drn	
	FROM employees
) as subquery
WHERE drn = 2 
```
