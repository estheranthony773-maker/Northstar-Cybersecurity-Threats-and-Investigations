# Northstar Cybersecurity Threats and Investigations

Cybersecurity Log Analysis & Threat Investigation
SQL Portfolio Project | MySQL | Tech Studio Academy Group A
Project Overview
Investigated cybersecurity login and alert records for Northstar Services (fictional) using MySQL. The analysis focuses on failed logins, IP reputation, employee and device activity, and unresolved security alerts to identify patterns requiring further review.
Project Scope
Item	Scope
Database tables	5
Main investigation areas	5
IP screening conditions	2
Failed-login screening threshold	5 or more
After-hours window	Before 09:00 or from 17:00
Reusable reporting views	1
Highest-failure dates specifically inspected	3


Five tables: employees, devices, login_logs, ip reputation, security alerts.
Key Business Questions & Aggregations
Area	Questions investigated	Aggregated outputs
Login activity	How many logins succeeded or failed? When and for whom were failures highest?	Total logins; success/failure counts and percentages; failed logins by weekday, hour, employee
IP reputation	Which IPs generated the most attempts? Were successful logins linked to high-risk IPs?	Attempts and failures by IP; counts by country and risk level
Employees & devices	Which employees used multiple devices? Which departments or devices had higher failure rates?	Distinct devices per employee; failed and total attempts; failure rates by department/device
Security alerts	Which alert types and severities were most common? Which high-priority alerts remained open?	Alert counts by severity, type, and status; resolution time in minutes/hours
Trends & prioritisation	Did failed logins increase compared with the previous day? Which open alerts need review?	Daily totals; day-over-day change and percentage change; ranked employees and prioritised alerts


Selected Numeric Rules in the SQL
Rule / parameter	Value used
Failed-login IP screening threshold	≥ 5 failures
IP risk condition	High Risk
After-hours start	Before 09:00
After-hours end	17:00 or later
Dates selected for targeted failed-login review	3 dates: 2026-09-14, 2026-09-25, 2026-09-29
Daily summary query	Top 10 dates by failed-login count


These are query criteria, not measured findings.
SQL Skills Demonstrated
Technique	Application
Filtering, sorting and grouping	WHERE, ORDER BY, GROUP BY, HAVING
Aggregation	COUNT(), SUM(), MIN(), MAX()
Conditional metrics	CASE, conditional SUM() / COUNT()
Combining tables	INNER JOIN, LEFT JOIN, CROSS JOIN
Multi-step queries	CTEs and subqueries
Ranking and period comparisons	DENSE_RANK(), LAG()
Time analysis	DATE(), DAYNAME(), HOUR(), TIMESTAMPDIFF()
Calculated rates	ROUND(), NULLIF()
Reusable reporting	CREATE OR REPLACE VIEW


Reusable Reporting Output
The script creates daily_security_summary:
Output column	Daily measure
activity_date	Login activity date
total_login_attempts	Total attempts
failed_login_attempts	Failed attempts
successfull_login_attempts	Successful attempts


The view supports daily monitoring and a query for the 10 dates with the highest failed-login counts.
Findings & Evidence Status
The SQL script defines analyses for login success/failure rates, high-failure accounts and IPs, high-risk successful logins, departmental/device failure rates, alert status and severity, alert resolution duration, and daily changes in failed logins.

Actual aggregate values are not included in the supplied SQL script. The script contains queries but no exported result tables or inserted dataset records. Therefore, totals, percentages, top-ranked employees/IPs, and alert counts cannot be reported accurately from this file alone.
Limitations
- Unusual activity and high-risk IP labels are indicators for investigation, not proof of an attack.
- The threshold of five failed attempts is a screening rule, not a confirmed security standard.
- Query outputs must be executed and validated against the source data before reporting numerical findings.
- Some calculations should be checked before use: the company-wide failure-rate query contains a status comparison with a leading space (' Failed'), and the department alert query's employee join should be validated.
Conclusion
This project demonstrates practical SQL for cybersecurity log investigation, aggregation, ranking, time-based trend analysis, and reusable reporting. It shows how structured queries can turn security records into measurable indicators for further investigation and management review.
