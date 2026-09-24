# 心血管类慢性疾病：疾病目录与 Skill 范围

讨论稿，2026-09-23。本文件为 app 的心血管 Skill 划定疾病与数据范围，不代表 app 已实现这些能力。疾病按适合慢病管理的常见程度大致分组；不同地区和人群的患病率不同，组内顺序不是严格排名。

## 服务对象与疾病范围

心血管 Skill 的基础评估面向 app 中的所有患者，不以现有疾病标签作为启动条件。患者可以已有 AD、PD、癌症或其他疾病，也可以尚无慢性病诊断；只有具备相关风险资料时才生成有依据的提示，资料不足时明确显示资料不足。已有临床确认的心血管疾病时，再启用对应长期管理规则。风险因素、尚待确认的异常检查、确诊疾病和既往急性事件必须分开记录。高血压既是首版管理对象，也是其他心血管疾病的风险因素。[WHO 心血管疾病说明（2025）](https://www.who.int/news-room/fact-sheets/detail/cardiovascular-diseases-%28cvds%29)。

首版拟完整支持成人高血压、慢性冠心病、心力衰竭和房颤。这四种疾病可以共存，却分别关注血压控制、缺血症状与既往冠脉事件、心脏功能与液体潴留、心律和卒中风险。心肌梗死与卒中通常是急性事件；事件后的长期用药、康复及再发预防进入慢病随访。卒中后的神经功能管理需要和负责神经疾病的同学明确分工。[AHA 心血管疾病概览](https://www.heart.org/en/health-topics/consumer-healthcare/what-is-cardiovascular-disease)。

扩展目录包括外周动脉疾病、脑血管疾病、心脏瓣膜病、其他心律失常、主动脉瘤、成人先天性心脏病、静脉血栓栓塞后的长期管理，以及地区差异明显的风湿性心脏病。先支持临床已确认的诊断、关键报告和既定随访计划；专病规则需逐项建立。[WHO 心血管疾病范围](https://www.who.int/news-room/fact-sheets/detail/cardiovascular-diseases-%28cvds%29)；[AHA 外周动脉疾病说明](https://www.heart.org/en/health-topics/peripheral-artery-disease/about-peripheral-artery-disease-pad)。

较少见或罕见疾病目录包括肥厚型心肌病、致心律失常性心肌病、肺动脉高压、遗传性长 QT 综合征、Brugada 综合征和家族性胸主动脉瘤。肥厚型心肌病并非极罕见；这些疾病的诊断和监测依赖专病检查。首版仅保存已确认诊断、专科资料与随访计划，不用通用高血压或心衰规则推断其病情。[NHLBI 心肌病资料](https://www.nhlbi.nih.gov/health/cardiomyopathy/types)；[NHLBI 肺动脉高压资料](https://www.nhlbi.nih.gov/news/2022/novel-blood-test-helps-evaluate-severity-pulmonary-arterial-hypertension-rare-lung)；[NIH 家族性胸主动脉瘤资料](https://medlineplus.gov/genetics/condition/familial-thoracic-aortic-aneurysm-and-dissection/)。

## 各病特有指标

**高血压**需要成对保存收缩压与舒张压、测量时间、家庭或诊室来源、设备与测量情境；家庭连续记录与医生确认的个人目标应分开。若有体位变化相关症状、妊娠、肾病或其他影响目标的情况，需要由临床资料说明。Skill 关注有质量的重复测量和长期趋势，避免用一次家用读数直接确诊或调整治疗。[AHA/ACC 高血压指南（2025）](https://professional.heart.org/en/science-news/2025-high-blood-pressure-guideline/top-things-to-know)。

**慢性冠心病**需要临床确认的冠脉诊断、心绞痛或活动相关胸部不适的发生时间与变化、既往心梗或支架/搭桥史、运动耐量、心电图、功能检查和冠脉影像报告。血脂与血压虽为共享指标，仍是冠心病随访的重要输入。药物记录应包含医生开立的降脂药和抗血小板药等适应证，不由 Skill 推断个人应服药物。[AHA/ACC 慢性冠心病患者信息（2023）](https://professional.heart.org/en/science-news/patient-resources/key-patient-messages-2023-chronic-coronary-disease-guideline)。

**心力衰竭**需要已确认的类型及超声心动图中的左室射血分数（LVEF），并持续记录同条件下的体重、气促、端坐呼吸或夜间憋醒、水肿、疲劳和活动能力变化。若有检查，还可保存 BNP 或 NT-proBNP、肾功能和电解质。利尿剂等药物与症状的时间关系有助于整理给医疗团队，但不能从体重变化单独推断液体潴留或改药。[AHA/ACC/HFSA 心衰指南（2022）](https://professional.heart.org/en/guidelines-statements/2022-ahaacchfsa-guideline-for-the-management-of-heart-failure-executive-summarycir0000000000001062)。

**房颤**需要心电图或医疗记录确认的诊断、发作或持续状态、心率与相关症状、既往卒中或短暂性脑缺血发作史、医生评估的血栓与出血风险、抗凝处方及复诊计划。穿戴设备的节律提示保存为待确认线索，不能自动升级为房颤确诊。抗凝药的漏服、出血报告和肾功能变化需及时供医疗团队核对。[AHA/ACC 房颤指南（2023）](https://professional.heart.org/en/science-news/2023-acc-aha-accp-hrs-guideline-for-the-diagnosis-and-management-of-atrial-fibrillation/top-things-to-know)。

**其他血管与结构性疾病**各有专用资料。外周动脉疾病关注行走诱发的腿部症状、足部伤口和临床踝肱指数（ABI）；瓣膜病关注超声中的具体瓣膜、病变类型与严重程度；主动脉瘤关注影像测得的部位、直径和随访间隔；脑血管病关注已确认事件类型、发生日期和出院后的预防计划。先记录原始报告和既定计划，再扩展自动分析。[AHA/ACC 外周动脉疾病指南（2024）](https://professional.heart.org/en/-/media/PHD-Files-2/Science-News/2/2024/2024-PAD-guideline-slide-set.pdf)；[AHA/ACC 瓣膜病指南](https://professional.heart.org/en/science-news/2020-acc-aha-guideline-for-the-management-of-patients-with-valvular-heart-disease/top-things-to-know)。

## 与其他疾病共享的指标

血压、心率、体重、腰围、血糖、HbA1c、血脂、肾功能、吸烟状态、活动、睡眠和实际用药由患者档案统一保存，同时提供给[代谢疾病文档](metabolic-diseases.md)所定义的 Skill。共享的意思是数据只记录一次，而不是两个 Skill 对同一数值作出同一种解释。例如体重的长期变化可用于代谢管理，短期变化还可能成为心衰随访线索；解释必须结合疾病背景、症状和测量时间。

## 计划中的 Skill 能力与规则

基础评估层读取所有符合条件患者的风险因素和可靠测量，说明是否缺少建议与医生讨论的检查、既有风险因素是否需要随访。只有已有诊断或经临床确认的事件才进入相应疾病管理层。任何单项症状、穿戴设备提示或一次测量都不自动生成冠心病、心衰或房颤诊断。

长期管理层按疾病汇总连续指标、症状变化、个人目标、既定治疗与复诊计划，追踪用药记录和检查缺项，并生成患者、照护者与医生可核对的摘要。药物知识覆盖降压药、降脂药、抗血小板药、抗凝药、心衰相关药物等类别及其用途；实际处方保存在 app 的统一药单，关联多个疾病的药物只显示一次。复杂相互作用、抗凝选择或剂量调整须依赖医疗团队和经过验证的专用资料。

多病共存时，Skill 与代谢 Skill 及其他疾病模块共享相关原始数据，合并重复提醒，并把潜在冲突呈现给医疗团队。胸痛、突发神经症状、晕厥或明显呼吸困难等急性情况进入统一安全流程，优先于常规趋势分析。每条输出应保留疾病状态、依据的数据及日期、规则版本、缺失资料与下一步建议；正式启用判断阈值前须核对适用人群、临床来源和例外，并经临床负责人确认。测试案例应包括无心血管诊断、有风险因素、单病种确诊，以及与 AD、PD、癌症或代谢疾病共存的患者。

正式 Skill 的资料包将保存疾病名称与同义词、输入字段与单位字典、药物类别和适应证说明、经确认的患者教育材料、临床指南来源与版本、规则适用条件，以及合成测试病例。患者的实际测量、处方、心电图与影像报告只保存在患者档案中，不写进通用 Skill 文件。
