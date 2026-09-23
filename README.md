# Healthcare SQL Analysis
Analysis of synthetic patient data (Synthea) using PostgreSQL, covering 
patient demographics, condition prevalence, healthcare costs, and utilization patterns.

## Dataset
- 1,163 patients
- 61,459 encounters
- 38,094 conditions
- 17,009 immunizations
- Source: [Synthea Synthetic Patient Generator](https://synthea.mitre.org/)

## Tools Used
PostgreSQL, pgAdmin

## Key Questions & Findings

### 1. Gender distribution of patients
\`\`\`sql
SELECT gender, COUNT(*) AS patient_count
FROM patients
GROUP BY gender;
\`\`\`
**Finding:** Total no. of male patients are 547 and female patients are 616"

![Gender Query](male-vs-female.png)

### 2. Top 10 most common conditions
\`\`\`sql
SELECT description, COUNT(*) AS condition_count
FROM conditions
GROUP BY description
ORDER BY condition_count DESC
LIMIT 10;
\`\`\`
**Finding:** The "conditions" table captures both medical diagnoses and social/ behavioral findings. The most frequently recorded entry was "Full-time employment (finding)" with 13,805 occurrences, followed by "Stress (finding)" 
(5,137) and "Part-time employment (finding)" (2,426). Among actual medical diagnoses, "Viral sinusitis (disorder)" was most common (1,233 cases), followed by "Acute viral pharyngitis" (678) and "Acute bronchitis" (571) 

![Top Conditions](top-10-conditions.png)

### 3. State/county with most patients
\`\`\`sql
SELECT state, county, COUNT(*) AS patient_count
FROM patients
GROUP BY state, county
ORDER BY patient_count DESC
LIMIT 10;
\`\`\`
**Findings:**
![State/county with most patients](State-and-county-with-most-patients.png)


