# Cardiovascular Chronic Disease Skill: Lab Presentation Summary

Discussion draft, 2026-09-23. Based on the [full cardiovascular disease plan](cardiovascular-diseases.md). The tables describe proposed capabilities, not features already implemented in the app.

## Purpose and Population

| Question | Current plan |
| --- | --- |
| Who is it for? | All patients in the app, including those with Alzheimer's disease (AD), Parkinson's disease (PD), cancer, another condition, or no established chronic disease diagnosis. An existing disease label is not required to start assessment. |
| What does it do? | Assess cardiovascular risks and follow-up gaps when relevant data are available; enter condition-specific long-term management after clinical confirmation. |
| How are states separated? | Risk factors, abnormal findings awaiting confirmation, confirmed disease, and prior acute events are recorded separately. |
| Full first-version support | Adult hypertension, chronic coronary disease, heart failure, and atrial fibrillation (AF). |
| Cross-condition boundaries | Hypertension is both a managed condition and a risk factor for other cardiovascular diseases. Long-term prevention after myocardial infarction or stroke belongs in follow-up; post-stroke neurological care requires coordination with the neurology lead. |

## Conditions and Disease-Specific Data

| Condition or state | Scope | Key disease-specific data | Management focus and limits |
| --- | --- | --- | --- |
| Hypertension | Full first-version support | Paired systolic/diastolic blood pressure, time, home or clinic source, device, measurement context, and clinician-confirmed individual target. | Review repeated measurements and long-term trends. A single home reading does not directly establish a diagnosis or justify a treatment change. |
| Chronic coronary disease | Full first-version support | Confirmed coronary diagnosis; timing and changes in chest discomfort; history of myocardial infarction, stent, or bypass surgery; exercise tolerance, ECG, functional tests, and coronary imaging. | Follow symptoms and secondary prevention. Record indications for prescribed drugs; the Skill does not decide which drugs an individual should take. |
| Heart failure | Full first-version support | Confirmed type and echocardiographic left ventricular ejection fraction (LVEF); serial weight, breathlessness, orthopnea, nocturnal breathlessness, edema, fatigue, and functional changes; BNP/NT-proBNP when available. | Organize changes alongside symptoms, kidney function, electrolytes, and medication history. Weight change alone does not establish fluid retention or justify changing medication. |
| Atrial fibrillation | Full first-version support | ECG- or medical-record-confirmed diagnosis, episode pattern, heart rate, symptoms, prior stroke/transient ischemic attack (TIA), clinician-assessed thrombotic and bleeding risks, and anticoagulant prescription. | Track missed doses, reported bleeding, kidney function, and follow-up. Wearable rhythm alerts remain clues awaiting confirmation. |
| Peripheral artery disease, cerebrovascular disease, valvular disease, other arrhythmias, aortic aneurysm, adult congenital heart disease, long-term care after venous thromboembolism, rheumatic heart disease | Expansion catalog | Depending on condition: ankle-brachial index (ABI), foot wounds, event dates, valve findings on echocardiography, aortic diameter on imaging, rhythm records, and original reports. | Initially record confirmed diagnoses and established follow-up plans; add disease-specific rules individually. |
| Hypertrophic cardiomyopathy, arrhythmogenic cardiomyopathy, pulmonary arterial hypertension, inherited long QT syndrome, Brugada syndrome, familial thoracic aortic aneurysm | Less common or rare-disease catalog | Confirmed name, specialist reports, relevant imaging, rhythm or genetic records, care team, and follow-up plan. | Initially store and display these records only. Do not infer disease status using generic hypertension or heart-failure rules. |

## Shared Data and Skill Rules

| Component | Data or capability | Output limits |
| --- | --- | --- |
| Shared patient data | Blood pressure, heart rate, weight, waist circumference, glucose, HbA1c, lipids, kidney function, smoking status, activity, sleep, and actual medication use. | Store each observation once in the patient record. Each Skill interprets it in light of the condition, symptoms, and measurement time. |
| Initial assessment | For any patient with relevant data, read risk factors and reliable measurements, then identify testing or follow-up gaps. | A single symptom, measurement, or wearable alert does not automatically create a diagnosis of coronary disease, heart failure, or AF. |
| Long-term management | For confirmed conditions, summarize trends, symptoms, personal targets, treatment, medication use, and follow-up plans. | Produce a summary that patients, caregivers, and clinicians can check. Activate disease-specific management only for confirmed conditions or events. |
| Medication knowledge | Cover the classes and purposes of antihypertensives, lipid-lowering agents, antiplatelets, anticoagulants, and heart-failure therapies. | Show a medication only once in the shared medication list. Complex interactions, anticoagulant selection, and dose changes require the clinical team or validated resources. |
| Multimorbidity and acute safety | Share data with metabolic and other modules, merge duplicate reminders, and flag potential conflicts. | Route chest pain, sudden neurological symptoms, syncope, or marked breathlessness through the app-wide safety process before routine trend analysis. |
| Formal Skill package | Disease names and synonyms, field and unit dictionary, medication knowledge, approved education materials, guideline versions, applicability criteria, and synthetic test cases. | Label outputs with evidence, dates, disease state, rule version, and missing data. Keep real patient measurements, prescriptions, ECGs, and imaging in the patient record. |

Detailed rationale and sources: [full cardiovascular disease plan](cardiovascular-diseases.md).
