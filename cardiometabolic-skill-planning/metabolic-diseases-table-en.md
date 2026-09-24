# Metabolic Chronic Disease Skill: Lab Presentation Summary

Discussion draft, 2026-09-23. Based on the [full metabolic disease plan](metabolic-diseases.md). The tables describe proposed capabilities, not features already implemented in the app.

## Purpose and Population

| Question | Current plan |
| --- | --- |
| Who is it for? | All patients in the app, including those with Alzheimer's disease (AD), Parkinson's disease (PD), cancer, another condition, or no established chronic disease diagnosis. An existing disease label is not required to start assessment. |
| What does it do? | Flag evidence-based metabolic risks when relevant data are available; support long-term management after a clinical diagnosis; identify missing information when data are insufficient. |
| How are states separated? | Screening clues, laboratory results in a risk range, and clinically confirmed diagnoses are recorded separately. A missing test is not a normal test. |
| Full first-version support | Adult type 2 diabetes, obesity, and dyslipidemia. |
| Limited first-version support | Prediabetes and metabolic syndrome enter risk and prevention pathways. For metabolic dysfunction-associated steatotic liver disease (MASLD), initially record confirmed diagnoses, reports, and follow-up gaps. |

## Conditions and Disease-Specific Data

| Condition or state | Scope | Key disease-specific data | Management focus and limits |
| --- | --- | --- | --- |
| Type 2 diabetes | Full first-version support | Laboratory fasting plasma glucose, HbA1c, oral glucose tolerance test; home glucose or continuous glucose monitoring (CGM) with measurement context; urine albumin-to-creatinine ratio (UACR), estimated glomerular filtration rate (eGFR), retinal and foot exams, and neuropathy records. | Track glucose trends and complication screening. Home glucose and CGM readings alone do not establish a diagnosis. |
| Obesity | Full first-version support | Height, serial weight, body mass index (BMI), waist circumference or waist-to-height ratio, and time frame of weight change; body-composition method when available. | Consider individual goals, treatment plans, and confirmed related complications. BMI is a screening measure, not a complete assessment. |
| Dyslipidemia | Full first-version support | LDL-C, HDL-C, triglycerides, total cholesterol, non-HDL-C; lipoprotein(a) and apolipoprotein B when measured. | Track lipid trends and prescribed treatment. Do not generate a prescription from a single result. |
| Prediabetes | Risk and prevention | Laboratory HbA1c, fasting plasma glucose, or oral glucose tolerance test results. | Preserve the evidence for the risk state; do not label it as confirmed type 2 diabetes. |
| Metabolic syndrome | Risk and prevention | Waist circumference, triglycerides, HDL-C, blood pressure, fasting glucose, and existing treatment that may affect these measures. | Show which criteria have evidence and which data are missing; do not conclude from incomplete information. |
| MASLD | Limited first-version support | Existing diagnosis; liver imaging or elastography reports; ALT, AST, platelet count, clinician-provided fibrosis assessment, and follow-up plan. | Record information and flag follow-up gaps. Full liver-disease rules require coordination with the responsible team. |
| Type 1 diabetes, familial hypercholesterolemia, severe hypertriglyceridemia, gout | Expansion catalog | Respectively: insulin treatment and acute risks; family history of premature cardiovascular disease and prior very high LDL-C; pancreatitis history; condition-specific treatment records. | Build separate rules for each condition. Type 1 diabetes must not inherit type 2 rules; agree on gout ownership with the rheumatology lead. |
| Phenylketonuria, glycogen storage diseases, urea cycle disorders, Gaucher disease, Fabry disease, Wilson disease, and selected mitochondrial disorders | Rare-disease catalog | Clinically confirmed name, original reports, care team, and follow-up plan; specialty data may include phenylalanine, ammonia, lactate, copper studies, enzyme activity, or genetic tests. | Initially recognize and store these conditions only. Do not apply automated rules designed for common metabolic diseases. |

## Shared Data and Skill Rules

| Component | Data or capability | Output limits |
| --- | --- | --- |
| Shared patient data | Demographics, weight, waist circumference, blood pressure, heart rate, glucose, HbA1c, lipids, kidney function, smoking status, diet, activity, sleep, actual prescriptions, and medication-taking records. | Store each observation once in the patient record, with date, units, source, and measurement context where needed. Each disease Skill may interpret it for its own purpose. |
| Initial screening | Read known risk factors, symptoms, and reliable laboratory tests; distinguish insufficient data, a reason to discuss screening, a result in a risk range, and a clinical diagnosis. | An AD, PD, or cancer label alone does not trigger a "possible diabetes" conclusion. State the specific evidence. Do not use home glucose or CGM as standalone diagnostic evidence. |
| Long-term management | For confirmed conditions, read individualized goals, serial measurements, treatment plans, symptoms, visits, and complication screening. | Summarize trends, data gaps, planned follow-up, and patient education. Do not independently change prescriptions or doses. |
| Medication knowledge | Include drug classes, indications, prescription reconciliation, medication-taking records, and patient-reported adverse effects. | A medication may relate to multiple conditions. Leave complex interactions and treatment changes to the clinical team or validated specialty resources. |
| Multimorbidity and safety | Share source data with cardiovascular and other modules, merge duplicate reminders, and flag potential conflicts. | Route acute risks through the app-wide safety process. Make each output traceable to data dates, relevant conditions, rule versions, and missing information. |
| Formal Skill package | Disease names and synonyms, field and unit dictionary, medication knowledge, approved education materials, guideline versions, applicability criteria, and synthetic test cases. | Keep real patient laboratory results, prescriptions, and medical records in the patient record, not in generic Skill files. Obtain clinical approval before enabling rules. |

Detailed rationale and sources: [full metabolic disease plan](metabolic-diseases.md).
