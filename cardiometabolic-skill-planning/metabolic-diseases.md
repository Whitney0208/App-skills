# 代谢类慢性疾病：疾病目录与 Skill 范围

讨论稿，2026-09-23。本文件为 app 的代谢 Skill 划定疾病与数据范围，不代表 app 已实现这些能力。疾病按适合慢病管理的常见程度大致分组；不同地区和人群的患病率不同，组内顺序不是严格排名。

## 服务对象与疾病范围

代谢 Skill 的基础筛查面向 app 中的所有患者，不以现有疾病标签作为启动条件。患者可以已有 AD、PD、癌症或其他疾病，也可以尚无慢性病诊断；只有具备相关风险资料时才生成有依据的提示，资料不足时明确显示资料不足。已有临床确认的代谢诊断时，Skill 再启用相应疾病的长期管理规则。筛查提示、检查结果处于风险范围、临床确诊是不同状态；缺少检查记录不能解释为检查正常。

首版拟完整支持成人 2 型糖尿病、肥胖和血脂异常。糖尿病前期属于血糖升高的风险状态；代谢综合征是腹型肥胖、血糖、血压和血脂等风险因素的组合。两者进入筛查与预防路径，不自动写成 2 型糖尿病确诊。代谢功能障碍相关脂肪性肝病（MASLD）也很常见，先支持记录已有诊断与报告、识别随访缺项；完整肝病规则须与负责肝病的同学协调。[ADA 糖尿病诊断标准（2026）](https://diabetesjournals.org/care/article/49/Supplement_1/S27/163926/2-Diagnosis-and-Classification-of-Diabetes)；[WHO 肥胖资料（2025）](https://www.who.int/news-room/fact-sheets/detail/obesity-and-overweight)；[NIDDK MASLD 资料](https://www.niddk.nih.gov/health-information/liver-disease/nafld-nash/definition-facts)。

扩展目录包括 1 型糖尿病、家族性高胆固醇血症、严重高甘油三酯血症，以及涉及嘌呤代谢的痛风。1 型糖尿病的胰岛素与急性风险管理不能沿用 2 型糖尿病规则；痛风的具体治疗边界应与风湿病负责人确认。家族性高胆固醇血症虽是遗传病，却并非极罕见，值得单独保留诊断和家族史入口。[NHLBI 家族性高胆固醇血症资料](https://www.nhlbi.nih.gov/events/2018/reducing-population-burden-familial-hypercholesterolemia-fh-prototype-translation)。

罕见遗传代谢病目录可收录苯丙酮尿症、糖原贮积病、尿素循环障碍、戈谢病、法布里病、威尔逊病和部分线粒体疾病。首版只识别临床已确认的名称，保存原始报告、治疗团队和随访计划，不套用常见代谢病的自动分析。各病所需资料不同，例如苯丙氨酸、氨、乳酸、铜代谢检查、酶活性或基因检测；这些由专病规则和专科团队定义。[NIH MedlinePlus 代谢病目录](https://medlineplus.gov/metabolicdisorders.html)。

## 各病特有指标

**2 型糖尿病**需要区分实验室空腹血浆血糖、糖化血红蛋白（HbA1c）、口服葡萄糖耐量试验与家庭血糖记录。家庭读数要保存测量时间、餐前或餐后情境、单位和设备来源；有连续血糖监测时再接入所用时间范围、范围内时间及低血糖事件。长期随访还要记录尿白蛋白/肌酐比（UACR）、估算肾小球滤过率（eGFR）、眼底检查、足部检查、已知神经病变或足溃疡史。家庭血糖仪或连续血糖监测读数不能单独用来确诊。[ADA 2026 诊断标准](https://diabetesjournals.org/care/article/49/Supplement_1/S27/163926/2-Diagnosis-and-Classification-of-Diabetes)；[ADA 2026 肾脏随访标准](https://diabetesjournals.org/care/article/49/Supplement_1/S246/163914/11-Chronic-Kidney-Disease-and-Risk-Management)；[ADA 2026 眼、神经与足部护理标准](https://diabetesjournals.org/care/article/49/Supplement_1/S261/163919/12-Retinopathy-Neuropathy-and-Foot-Care-Standards)。

**肥胖**需要身高、连续体重、BMI、腰围或腰高比，以及体重变化的时间范围。若有可信的身体组成测量，可保存方法与结果。还需记录医生确认的相关并发症、患者同意的目标和正在实施的管理方案。BMI 是筛查信息；对脂肪分布和个人情况的判断需要更多资料。[ADA 成人肥胖评估标准（2026）](https://diabetesjournals.org/docm-care/collection/26328/Standards-of-Care-in-Overweight-and-Obesity-2026)。

**血脂异常**需要带日期和单位的 LDL-C、HDL-C、甘油三酯、总胆固醇和非 HDL-C；若已检测，可保存脂蛋白(a)与载脂蛋白 B。家族性高胆固醇血症还要记录临床诊断、早发心血管病家族史、既往极高 LDL-C 结果和可用的遗传报告。严重高甘油三酯血症要保留胰腺炎病史和检验来源。[AHA/ACC 血脂异常指南（2026）](https://professional.heart.org/en/science-news/2026-guideline-on-the-management-of-dyslipidemia)。

**MASLD**先记录已有诊断、肝脏影像或弹性成像报告、ALT、AST、血小板、医生给出的纤维化分层和后续复查计划。FIB-4 等风险工具需要检查适用条件、完整输入和来源版本；本阶段不凭一项肝酶异常自动判断脂肪肝或肝纤维化。[AASLD MASLD 评估资料](https://www.aasld.org/liver-fellow-network/core-series/clinical-pearls/spare-me-jab-noninvasive-assessment-patients-masld)。

**糖尿病前期与代谢综合征**分别保留构成依据。前者保存实验室 HbA1c、空腹血浆血糖或口服葡萄糖耐量试验结果；后者保存腰围、甘油三酯、HDL-C、血压和空腹血糖，以及既有治疗是否影响这些数值。Skill 要显示用了哪些指标、哪些仍缺失，不能凭不完整资料宣布患有代谢综合征。[ADA 2026 诊断标准](https://diabetesjournals.org/care/article/49/Supplement_1/S27/163926/2-Diagnosis-and-Classification-of-Diabetes)；[NHLBI 代谢综合征说明](https://www.nhlbi.nih.gov/health/metabolic-syndrome)。

## 与其他疾病共享的指标

患者基本资料、体重、腰围、血压、心率、血糖、HbA1c、血脂、肾功能、吸烟状态、饮食、活动和睡眠可能同时服务代谢与心血管 Skill。一个测量结果在患者档案中只保存一次；各 Skill 读取同一记录并说明自己的解释目的。每条结果必须保留日期、单位、检测或设备来源，以及必要的测量情境。实际处方和服药记录也由 app 统一保存，并允许一项药物关联多个适应证。

## 计划中的 Skill 能力与规则

筛查层读取患者的已知风险因素、症状与可靠化验，区分资料不足、值得与医生讨论筛查、已有实验室风险范围结果，以及临床确认诊断。AD、PD、癌症等其他疾病标签本身不会触发“疑似糖尿病”结论；提示必须说明所依据的具体风险因素或检查结果。对于无明确症状的异常结果，输出待临床确认的说明；不把家庭血糖或 CGM 当作确诊依据。[ADA 2026 筛查与诊断标准](https://diabetesjournals.org/care/article/49/Supplement_1/S27/163926/2-Diagnosis-and-Classification-of-Diabetes)。

长期管理层根据已确认的疾病分别读取医生给出的个体目标、连续测量、治疗计划、症状、复诊与并发症检查。它生成趋势摘要、数据缺口、既定随访提醒和患者教育内容。用药知识覆盖相关药物类别、处方核对、服药记录与患者报告的不良反应；处方变更、剂量建议和复杂相互作用判断需要医疗团队或经过验证的专用资料支持。

多病共存时，Skill 与[心血管疾病文档](cardiovascular-diseases.md)及其他疾病模块共享相关记录。app 合并重复提醒，并标出潜在冲突供医疗团队查看。每条输出应能追溯到患者数据的来源和日期、适用疾病、规则版本、缺失资料与下一步建议；急性风险由统一的安全流程处理。正式写规则前，需要逐条核对临床来源、适用人群、例外条件，并由临床负责人确认；测试案例应覆盖无诊断、有风险因素、已确诊，以及与 AD、PD、癌症等疾病共存的患者。

正式 Skill 的资料包将保存疾病名称与同义词、输入字段与单位字典、药物类别和适应证说明、经确认的患者教育材料、临床指南来源与版本、规则适用条件，以及合成测试病例。患者的实际化验、处方和病历只保存在患者档案中，不写进通用 Skill 文件。
