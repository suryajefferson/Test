n
## 1
### Top 10 highest paying data analyst job details with company names in India or work from home 
<details>
<summary style="font-size: 1.em;">click for <span style="font-size: 1.15em;">Detailed Question </span></summary>


- **Question:** What are the top-paying Data Analyst jobs?
- **Details:**
    - Identify the top 10 highest-paying *Data Analyst* roles available either in India or remotely.
    - Focus on job postings with specified salaries (remove nulls).
    - Include the company names of the top 10 roles.
- **Why?** Highlight the top-paying opportunities for *Data Analysts*, offering insights into employment options and location flexibility.
</details>

<details>
<summary style="font-size: 1.em;">click for <span style="font-size: 1.45em;font-weight: bold;">Code </span></summary>

``` sql
SELECT 
    job_postings_fact.job_id,
    job_title,
    salary_year_avg,
    company_dim.name AS company,
    job_location,
    job_schedule_type,
    job_posted_date
FROM 
    job_postings_fact
LEFT JOIN company_dim ON job_postings_fact.company_id = company_dim.company_id
WHERE 
    job_title_short = 'Data Analyst' AND 
    (job_location LIKE '%India' OR job_work_from_home = TRUE) AND
    salary_year_avg IS NOT NULL
ORDER BY 
    salary_year_avg DESC
LIMIT 10;
```
<details>
<summary style="font-size: 1.em;">click for <span style="font-size: 1.15em;">Results</span></summary>

| job_id | job_title | salary_year_avg | company | job_location | job_schedule_type | job_posted_date |
| --- | --- | --- | --- | --- | --- | --- |
| 226942 | Data Analyst | 650000.0 | Mantys | Anywhere | Full-time | 2023-02-20 15:13:33 |
| 547382 | Director of Analytics | 336500.0 | Meta | Anywhere | Full-time | 2023-08-23 12:04:42 |
| 552322 | Associate Director- Data Insights | 255829.5 | AT&T | Anywhere | Full-time | 2023-06-18 16:03:12 |
| 99305 | Data Analyst, Marketing | 232423.0 | Pinterest Job Advertisements | Anywhere | Full-time | 2023-12-05 20:00:40 |
| 1021647 | Data Analyst (Hybrid/Remote) | 217000.0 | Uclahealthcareers | Anywhere | Full-time | 2023-01-17 00:17:23 |
| 168310 | Principal Data Analyst (Remote) | 205000.0 | SmartAsset | Anywhere | Full-time | 2023-08-09 11:00:01 |
| 731368 | Director, Data Analyst - HYBRID | 189309.0 | Inclusively | Anywhere | Full-time | 2023-12-07 15:00:13 |
| 310660 | Principal Data Analyst, AV Performance Analysis | 189000.0 | Motional | Anywhere | Full-time | 2023-01-05 00:00:25 |
| 1749593 | Principal Data Analyst | 186000.0 | SmartAsset | Anywhere | Full-time | 2023-07-11 16:00:05 |
| 387860 | ERM Data Analyst | 184000.0 | Get It Recruit - Information Technology | Anywhere | Full-time | 2023-06-09 08:01:04 |

</details>

<details>
<summary style="font-size: 1.em;">click for <span style="font-size: 1.15em;">Insights </span></summary>


**Highest Salaries:**

- *Data Analyst* roles have the highest salary at 650,000, indicating premium compensation for these positions.

**Notable Positions:**

- *Director Of Analytics* at Meta offers a substantial salary of 336,500, showing a high-value role in a prominent company.
- *Associate Director - Data Insights* at AT&T also commands a high salary of 255,829.5.

**Recent Postings:**

- Most job postings are recent, with dates ranging from January 2023 to December 2023, suggesting active hiring in the data field.



</details>
