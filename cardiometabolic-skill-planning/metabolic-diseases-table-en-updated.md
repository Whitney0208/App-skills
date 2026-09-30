# Metabolic Chronic Disease Skills: Updated Disease and Indicator Plan

Working draft, 2026-09-30. This is a separate update to [the original English presentation table](metabolic-diseases-table-en.md). It expands the existing 17 conditions or risk states into individual rows and incorporates the local MIMIC-IV Note audit and clinical-source additions discussed after that audit. The original table remains unchanged.

This document defines data the app should be able to receive and interpret. It does not describe features already implemented, a universal testing panel, or a clinically validated decision engine. Diagnostic evidence, routine monitoring, and investigations prompted by symptoms must remain separate. Test selection depends on diagnosis, subtype, age, pregnancy, treatment, and clinical context.

## Population and Implementation Scope

| Topic | Updated plan |
| --- | --- |
| Population | All patients in the app, including people with AD, PD, cancer, other conditions, multiple conditions, or no established chronic disease diagnosis. An existing metabolic diagnosis is not required to assess relevant risk information. |
| First-version full support | Adult type 2 diabetes, obesity, and dyslipidemia remain the proposed first-version priorities. The broader field catalog below does not expand implementation commitments automatically. |
| Risk and prevention | Prediabetes and metabolic syndrome remain distinct from a confirmed diabetes diagnosis. |
| Limited first-version support | MASLD: preserve existing diagnoses and reports and identify follow-up gaps. Coordinate full liver-disease rules with the responsible team. |
| Expansion conditions | Type 1 diabetes, familial hypercholesterolemia, severe hypertriglyceridemia, and gout require their own rules. Coordinate gout management boundaries with the rheumatology lead. |
| Rare diseases | Initially preserve specialist-confirmed diagnoses, subtypes, original reports, care teams, and follow-up plans. The expanded fields below describe future specialist-informed support, not automatic interpretation in the first version. |
| Multimorbidity | Share the same observations with cardiovascular and other Skills. A coexisting condition alone does not establish a metabolic diagnosis. Merge duplicate reminders and preserve any conflicting interpretations for review. |

## What the Evidence Labels Mean

| Evidence layer | What it supports | What it does not establish |
| --- | --- | --- |
| Original planning fields | Fields already present in the original English table or the full metabolic plan. | Their presence in every patient's record or successful implementation in the app. |
| Local note audit | Whether predefined terms and candidate values could be retrieved from selected patients' disease-associated admissions. Disease-specific coverage is reported in the [audit summary](metabolic-note-audit/SUMMARY.md). | Independent confirmation of every diagnosis, completion of every mentioned examination, correct interpretation of every number, or completeness of a disease's indicator list. |
| Clinical-source additions | Additional candidate fields supported by the clinical references linked below. | Validation against the local patient sample. These additions extend beyond the audit's original 50-field dictionary. |
| Proposed app rules | How to preserve evidence, distinguish states, and present gaps or trends. | Clinically approved diagnostic thresholds, monitoring intervals, medication doses, or autonomous treatment changes. |

The local audit was a predefined-field coverage review. It was not an unrestricted search for every potentially missing biomarker in the notes. A field may have been searched without producing an eligible result. A narrative mention, a numeric candidate, a planned test, a negative statement, and a comparison threshold are different evidence types.

## Conditions and Specific Indicators

The fields in this table combine the existing plan with clinical-source additions. Diagnostic genetic or enzyme reports generally belong to the diagnostic record; their inclusion does not imply repeated testing at each follow-up. Conditional investigations are marked in the relevant cell.

| Condition or state | Core measurements and diagnostic evidence | Follow-up, complications, and conditional additions |
| --- | --- | --- |
| **Type 2 diabetes** | Laboratory fasting plasma glucose and HbA1c; oral glucose tolerance testing (OGTT) when needed for diagnosis or clarification; home glucose with meal and device context. If CGM is used, retain time in range (TIR), time below range (TBR), time above range (TAR), mean glucose, and variability. | Hypoglycemia episodes and assistance required; UACR, creatinine, and eGFR; retinal examination findings and existing retinopathy; foot sensation, pedal pulses, neuropathy, and ulcers. Consider vitamin B12 assessment according to metformin exposure and clinical findings. Home glucose and CGM alone do not establish the diagnosis. [ADA assessment](https://doi.org/10.2337/dc26-S004), [glycemic monitoring](https://doi.org/10.2337/dc26-s006), [diagnosis](https://diabetesjournals.org/care/article/49/Supplement_1/S27/163926/2-Diagnosis-and-Classification-of-Diabetes). |
| **Obesity** | Height, serial weight, BMI, waist circumference or waist-to-height ratio; amount and percentage of weight change and the time interval. Retain body-composition results and method when clinically indicated or already available. | Blood pressure, glycemic and lipid results, relevant liver findings, sleep-apnea symptoms, mobility and joint limitations, diet, activity, and weight-related treatment. Body-composition imaging is not a universal requirement. [NICE assessment guidance](https://www.nice.org.uk/guidance/ng246/chapter/Identifying-and-assessing-overweight-obesity-and-central-adiposity). |
| **Dyslipidemia** | LDL-C, HDL-C, triglycerides, total cholesterol, and non-HDL-C; lipoprotein(a); apolipoprotein B when appropriate to risk assessment. Record whether LDL-C was measured directly or calculated. | Prior cardiovascular events and family history; lipid trends before and after treatment; prescribed therapy and tolerability; evaluation of secondary causes when appropriate. Preserve collection conditions and treatment context. [2026 ACC/AHA guidance](https://www.acc.org/About-ACC/Press-Releases/2026/03/13/18/01/ACCAHA-Issue-UpDated-Guideline-for-Managing-Lipids-Cholesterol). |
| **Prediabetes** | Laboratory HbA1c, fasting plasma glucose, or 2-hour glucose during OGTT; repeat results and the evidence supporting the recorded risk state. | Weight, BMI, waist, blood pressure, and lipids; diabetes family history, previous gestational diabetes, and relevant medications. Preserve whether the state persists, improves, or is followed by a clinically confirmed diabetes diagnosis. Do not treat a later note alone as proof of biological progression. [ADA diagnosis and classification](https://diabetesjournals.org/care/article/49/Supplement_1/S27/163926/2-Diagnosis-and-Classification-of-Diabetes). |
| **Metabolic syndrome** | Waist circumference, triglycerides, HDL-C, blood pressure, and fasting glucose; existing treatment affecting these components. | Record the criteria set used, its population applicability, and the date and evidence for each component. Do not combine incompatible measurements or infer a complete diagnosis from missing components. [NHLBI diagnostic overview](https://www.nhlbi.nih.gov/health/metabolic-syndrome/diagnosis). |
| **MASLD** | Existing diagnosis and evidence of hepatic steatosis; ALT, AST, and platelet count; an existing FIB-4 result and its inputs, including age and measurement dates; elastography/liver stiffness and other fibrosis tests when appropriate. | Cardiometabolic risk factors, alcohol exposure, and alternative liver-disease explanations; clinician-provided fibrosis stage. Advanced liver disease may require bilirubin, albumin, INR, and specialist surveillance. The app should not calculate or interpret FIB-4 without checking applicability and complete inputs. Preserve legacy NAFLD/NASH labels separately until clinically reassessed. [EASL–EASD–EASO guidance](https://doi.org/10.1007/s00125-024-06196-3). |
| **Type 1 diabetes** | HbA1c, home glucose, CGM metrics, and insulin regimen/delivery records. Preserve islet autoantibodies, C-peptide, and concurrent glucose when obtained to clarify classification. | Hypoglycemia and awareness; blood/urine ketones during relevant illness or suspected ketosis, with associated acute-care findings. UACR, eGFR, retinal and foot surveillance; thyroid assessment and celiac testing as appropriate. Keep classification tests separate from routine monitoring. [ADA classification](https://diabetesjournals.org/care/article/49/Supplement_1/S27/163926/2-Diagnosis-and-Classification-of-Diabetes), [assessment](https://doi.org/10.2337/dc26-S004), [glycemic risks](https://doi.org/10.2337/dc26-s006). |
| **Familial hypercholesterolemia** | Untreated or historical highest LDL-C and the current lipid profile; personal and family premature cardiovascular disease with age at onset; tendon xanthomas and relevant examination findings; available genetic reports. | Treatment response, known atherosclerotic disease, assessment of relatives, and secondary causes of high LDL-C. Generic family-history text does not establish premature cardiovascular disease in a relative. Molecular results and clinical diagnosis should remain distinguishable. [GeneReviews](https://www.ncbi.nlm.nih.gov/books/NBK174884/?report=reader). |
| **Severe hypertriglyceridemia** | Fasting triglycerides and repeat trends; full lipid profile; glucose/HbA1c; pancreatitis history and the evidence supporting the recorded severity. | Alcohol, diet, medications, kidney disease, and other secondary causes. During suspected acute pancreatitis, preserve clinically obtained laboratory and imaging results. Specialist investigations may be needed for suspected inherited subtypes. Do not classify ordinary hypertriglyceridemia as severe from an unspecified disease label. [ACC consensus](https://www.acc.org/Latest-in-Cardiology/ten-points-to-remember/2021/07/27/21/04/2021-ACC-ECDP-Hypertriglyceridemia). |
| **Gout** | Serum urate and serial trends; flare frequency, dates, joint locations, duration, and pain; tophus location and change. Preserve synovial-fluid crystal findings or imaging when obtained to clarify diagnosis. | Creatinine, eGFR, kidney-stone history, prescribed urate-lowering therapy, adherence, adverse effects, and treatment-specific monitoring. A serum urate result must be interpreted with the clinical history. [NICE gout guidance](https://www.nice.org.uk/guidance/ng219/chapter/Recommendations). |
| **Phenylketonuria / PAH deficiency** | Blood phenylalanine (Phe), tyrosine (Tyr), existing PAH genetic reports, and specialist diagnostic interpretation; dietary protein/Phe intake, prescribed medical nutrition, and treatment. | Growth, weight, nutritional status, and age-/risk-appropriate nutritional laboratory assessment, including blood count, ferritin, or vitamin B12 when appropriate; cognition, attention, mood, and daily functioning; pregnancy or pregnancy planning. [GeneReviews](https://www.ncbi.nlm.nih.gov/books/NBK1504/?report=classic). |
| **Glycogen storage diseases** | Record the subtype and existing molecular/enzyme diagnosis first. Depending on hepatic subtype: glucose, hypoglycemia, lactate, ketones, triglycerides, urate, and liver tests. Depending on muscle subtype: creatine kinase (CK), muscle strength, and exercise tolerance. | Subtype-specific liver size/nodule imaging, kidney function and urine protein, ECG and echocardiography. Pompe disease and other relevant muscle phenotypes may require respiratory function, respiratory-muscle, and swallowing assessments. No single panel applies to all subtypes. [Type I](https://www.ncbi.nlm.nih.gov/sites/books/NBK1312/), [type III](https://www.ncbi.nlm.nih.gov/books/NBK26372/), [Pompe disease](https://www.ncbi.nlm.nih.gov/books/NBK1261/?report=reader). |
| **Urea cycle disorders** | Ammonia; plasma amino-acid profile with subtype-relevant glutamine, citrulline, arginine, and other results; urinary orotic acid when needed for classification; existing genetic reports. | Hyperammonemic episodes and triggers, neurocognitive status, protein/energy intake, nutrition and growth; liver tests, coagulation, electrolytes, and blood gases as clinically indicated. Preserve specimen handling and collection context. This proposed expansion has no eligible disease cohort in the current local audit. [GeneReviews](https://www.ncbi.nlm.nih.gov/sites/books/NBK1217/). |
| **Gaucher disease** | Diagnostic reports: glucocerebrosidase activity and GBA1 findings. Monitoring data: hemoglobin, platelet count, liver/spleen volumes, liver enzymes, and specialist Lyso-Gb1 results when available. | Bone pain, crises, fractures and osteonecrosis; bone MRI or bone density when indicated; bleeding and fatigue; subtype-specific neurologic and pulmonary involvement; enzyme-replacement or substrate-reduction treatment records. These organ and biomarker additions were not systematically extracted in the local audit. [Diagnosis](https://www.ncbi.nlm.nih.gov/books/NBK1269/), [surveillance](https://www.ncbi.nlm.nih.gov/books/NBK1269/table/gaucher.T.gaucher_disease_recommended_su/). |
| **Fabry disease** | Diagnostic reports: alpha-galactosidase A activity and GLA findings; specialist Lyso-Gb3 results. Renal data: creatinine, eGFR, and urinary albumin/protein. | ECG, echocardiography, and cardiac MRI when indicated; neuropathic pain, stroke/TIA, hearing and gastrointestinal manifestations. Normal enzyme activity alone cannot exclude disease in females. Organ-specific assessment must follow the specialist plan. [GeneReviews](https://www.ncbi.nlm.nih.gov/books/NBK1292/?report=reader). |
| **Wilson disease** | Ceruloplasmin, serum copper, and 24-hour urinary copper as separate measurements, with treatment and collection context; existing ATP7B results, slit-lamp/Kayser–Fleischer ring findings, and other specialist diagnostic investigations when needed. | ALT, AST, bilirubin, albumin, INR, and blood count; neurologic and psychiatric manifestations; treatment-specific renal, urine, and adverse-effect monitoring. Do not combine different copper tests into one undifferentiated clinical value. [GeneReviews](https://www.ncbi.nlm.nih.gov/sites/books/NBK1512/?report=reader). |
| **Selected mitochondrial disorders** | Specific syndrome/subtype and mitochondrial or nuclear genetic reports; lactate in diagnostic or relevant clinical contexts, with pyruvate or blood gases when indicated; CK, muscle strength, and exercise tolerance. | Organ-directed ECG/echocardiography, glucose/HbA1c, kidney/liver tests, hearing, vision, neurologic/cognitive, nutritional, swallowing, and respiratory assessment. Lactate alone neither establishes the diagnosis nor measures severity across all subtypes. [Mitochondrial Medicine Society consensus](https://pmc.ncbi.nlm.nih.gov/articles/PMC7804217/). |

## Shared Patient Data

Shared fields are stored once and linked to all relevant disease Skills. Their presence in this table does not make every laboratory test mandatory for every patient.

| Shared domain | Data to retain |
| --- | --- |
| Population and applicability | Age, clinically relevant sex information, pregnancy/pregnancy planning, confirmed conditions and subtypes, diagnosis dates, and relevant family history. |
| Measurements | Height, weight, BMI, waist circumference, blood pressure, heart rate, and time-stamped trends. Preserve measured versus calculated values. |
| Laboratory observations | Available glucose/HbA1c, lipid fractions, creatinine/eGFR, urinary albumin/protein; liver tests, blood count, and electrolytes according to condition and treatment. |
| Lifestyle and nutrition | Diet, alcohol, smoking, activity, sleep, feeding difficulties, and prescribed disease-specific nutrition. |
| Treatment and actual use | Medication, dose, frequency, indication, start/stop dates, actual use, missed doses, and patient-reported adverse effects. A medication may serve several conditions. |
| Symptoms and function | Onset, frequency, severity, and relevant triggers; mobility, cognition, daily functioning, and caregiver assistance. |
| Examination and follow-up status | Completed, planned, pending result, or not supplied; examination findings, responsible clinical team, individualized goals, and the existing follow-up plan. |
| Observation provenance | Original test name, value, units, specimen, measurement date/time, laboratory/device, reference interval when supplied, and relevant fasting/meal/treatment context. A note date is not automatically a measurement date. |
| Diagnostic evidence | Clinician-confirmed diagnosis, suspected condition, laboratory risk state, or self-reported history; patient disease versus family/carrier status; original disease wording, subtype conflicts, and subsequent clinical clarification. |

## Changes Relative to the Original English Table

| Addition or clarification | Relationship to the original plan | Local evidence and remaining work |
| --- | --- | --- |
| Serum urate for gout | A specific laboratory field added to the English table's previously broad treatment-record entry. It was added to the audit dictionary before extraction. | Among 50 selected gout patients, 4 had qualifying related text and 1 had a numeric candidate. This supports retaining it as a candidate field, not claiming that one record validates a complete gout rule. |
| Hypoglycemia, retinopathy, and foot-ulcer records | Make existing complication concepts explicit and distinguish disease findings from examination completion. Hypoglycemia and foot ulcers were already mentioned in the full Chinese plan. | Type 2 diabetes: qualifying text for hypoglycemia in 9/50, retinopathy in 7/50, and foot ulcers in 4/50. These are text-coverage counts, not independently confirmed complication prevalence. |
| Type 1 acute-risk fields | Expand the original phrase “acute risks” into hypoglycemia and ketone/ketosis-related records. | Qualifying hypoglycemia text in 21/50 and ketone/ketosis-related text in 25/50. The latter does not mean 25 patients had confirmed diabetic ketoacidosis. |
| Creatinine | Makes the original shared “kidney function” category explicit; not an entirely new clinical domain. | Numeric candidates in 43/50 gout patients. Renal interpretation and treatment relevance still require clinical context. |
| Ceruloplasmin and separately identified copper tests | Makes the original “copper studies” category more specific. | One ceruloplasmin numeric candidate among 5 Wilson disease patients. The audit grouped copper-related terms; separate analytes and collection conditions are a proposed schema improvement. |
| CGM statistics, organ assessments, and rare-disease biomarkers | Clinical-source additions beyond the audit dictionary, including TIR/TBR/TAR, relevant organ surveillance, Lyso-Gb1, and Lyso-Gb3. | Not systematically tested against the local sample. Retain as proposed fields pending specialist review and further data mapping. |
| Disease and result states | Refine existing source, context, and missing-data rules. | The audit flagged 7 type-conflict memberships, 2 prediabetes patients with later typed-diabetes records, 2 memberships with resolved-history wording, 2 with self-reported wording, and 1 with pregnancy wording in diagnostic evidence. These flags require interpretation. |
| Dataset-specific aliases | Retrieval improvements, not new biomarkers. | Added LDLcalc, LDLmeas, Triglyc, and Cholest; kept CHOL/HD ratio distinct from total cholesterol. Clinical thresholds in templates were separated from measured-value candidates. |

## Local Audit Coverage and Limits

The audit scanned 331,793 discharge summaries and 2,321,355 radiology reports from the supplied MIMIC-IV Note 2.2 directory. It selected up to 50 distinct patients per condition using a fixed hash order, before assessing indicator completeness. Eligibility relied on explicit disease wording in past medical history or discharge diagnoses. Indicator retrieval was limited to admissions with qualifying disease evidence.

| Condition or group | Selected patients | Interpretation |
| --- | ---: | --- |
| Type 2 diabetes | 50 | Text-screened cohort; not independently adjudicated for every diagnosis. |
| Obesity | 50 | Same sampling method. |
| Dyslipidemia | 50 | Same sampling method. |
| Prediabetes | 50 | Historical and later diagnostic states retained for review. |
| Metabolic syndrome | 50 | Component completeness was not required for sampling. |
| MASLD | 0 | No eligible explicit modern-label cohort under these rules. |
| Type 1 diabetes | 50 | Type conflicts retained as review flags. |
| Familial hypercholesterolemia | 9 | Below the 50-patient target. |
| Severe hypertriglyceridemia | 8 | Below target; unspecified hypertriglyceridemia was not automatically upgraded. |
| Gout | 50 | Same sampling method. |
| Phenylketonuria | 1 | Below target. |
| Glycogen storage diseases | 2 | Below target; cannot represent all subtypes. |
| Urea cycle disorders | 0 | No eligible cohort; evaluation or differential-diagnosis mentions did not qualify. |
| Gaucher disease | 3 | Below target; carrier-only wording excluded. |
| Fabry disease | 2 | Below target. |
| Wilson disease | 5 | Below target. |
| Selected mitochondrial disorders | 37 | Below target; heterogeneous labels and some self-reported history remain. |
| Legacy NAFLD/NASH supplement | 50 | Additional historical-label group, not counted as confirmed MASLD or as a new disease in the original 17-condition catalog. |

Including the legacy supplement, the audit covered 464 distinct patients and 467 patient–disease memberships. A patient could belong to more than one group. The 9,739 retained indicator excerpts and 467 primary disease-evidence records were reconciled with the source files: 10,206 retained evidence records in total. Fourteen regression tests passed. This establishes extraction traceability and count consistency, not clinical validity.

Patients below the target are the result of the specified text-screening rules, not proof that the database contains no other affected patients. Additional full-note keyword matches are retained locally for review and include differentials, family history, test indications, and unrelated uses of abbreviations. Missing extracted fields cannot be interpreted as normal findings, unperformed examinations, or reasons to remove a clinically appropriate field.

The audit did not systematically extract all measurement dates, fasting/meal states, device details, medication doses, adherence, population eligibility, or the expanded specialist fields in this document. In particular, age and pregnancy applicability were not independently checked against structured demographic tables. Source notes do not fully represent longitudinal outpatient or home monitoring.

Aggregate findings are available in the [audit summary](metabolic-note-audit/SUMMARY.md); methods and reproducible code are described in the [audit README](metabolic-note-audit/README.md), and the [review notes](metabolic-note-audit/REVIEW.md) document corrections and limitations. Patient identifiers and excerpts remain in the local private output directory and are not included in this document.

## Skill Behavior and Clinical Review

| Skill function | Planned behavior and limits |
| --- | --- |
| Initial risk assessment | Use relevant risk factors, symptoms, and reliable test results. Distinguish insufficient information, a reason to discuss screening, a laboratory risk state, and confirmed disease. Do not infer diabetes from AD, PD, cancer, or another diagnosis alone. |
| Long-term management | Summarize trends against clinician-defined goals, preserve treatment and symptom history, and identify gaps in an existing follow-up plan. |
| Medication knowledge | Support medication reconciliation, indications, actual-use records, and reported adverse effects. Independently changing doses or handling complex interactions requires validated clinical support beyond this field catalog. |
| Multiple conditions | Reuse observations, merge duplicate reminders, and surface conflicts for clinical review. Retain the condition and evidence behind each interpretation. |
| Acute risk | Route relevant acute findings through the app's shared safety process. Do not derive alert thresholds from this convenience sample. |
| Rule specification | Before enabling a rule, define its source/version, applicable population and subtype, required inputs, exclusions, missing-data handling, clinical review status, and test cases. Diagnostic thresholds and follow-up intervals are not specified by this table. |
| Formal Skill package | Retain disease definitions and synonyms, input/unit dictionaries, medication knowledge, approved patient education, source versions, interpretation and output rules, and synthetic test cases. Real patient records belong in patient data storage, not in reusable Skill instructions. |

This update is a planning document. The expanded indicator catalog, implementation status, local extraction coverage, and clinical approval status must remain separate as the app develops.
