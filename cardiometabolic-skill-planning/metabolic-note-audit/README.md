本地 MIMIC-IV Note 代谢病指标核对

GitHub 本次仅发布本说明、SUMMARY.md 和 REVIEW.md。下文提到的脚本、private 目录和原始数据仍保存在本地；复现命令需要本地完整代码与获准使用的数据，不能仅凭本仓库中的文档运行。

本目录对照上一级 metabolic-diseases.md 中的 17 类疾病或风险状态，目标为每类抽取 50 名不同患者。只读取用户指定的 MIMIC-IV Note 2.2，不联网下载，不调用模型或其他外部 API。脚本均使用 Python 标准库，无额外依赖。

当前结果请读 SUMMARY.md 和 private/final/REPORT.md。private/final/field-coverage.csv 保存逐病、逐指标的患者覆盖数。private/final/patient-index.csv 保存入组选取依据。private/final/indicator-evidence.csv 保存指标原文、患者和住院关联、文书编号、行号、字符位置、数值候选与原文明确出现的单位。病例文件含受限病历信息，必须留在本地，不能上传到公开 GitHub。

从本目录重新运行时，使用一个尚不存在的输出目录，例如：

```bash
python3 run_audit.py --output private/reproduction --target 50
```

完整流程由 run_audit.py 串行运行。scan_cohorts.py 校验原始压缩文件的发布方 SHA256，逐条扫描出院小结，保存病名匹配与拒绝原因，再按固定种子和患者 ID 的 SHA256 排序抽样。extract_indicators.py 在入组证据所在的同次住院内提取出院小结与影像报告。validate_results.py 独立重算患者分母和覆盖数，并再次读取原始文件，核实每一条保留证据的文字和位置。write_summary.py 只在验证通过后生成不含患者标识和原文的汇总。

每次运行保留版本、代码校验值、原规划文档校验值、源文件校验值和选中患者清单。已有运行不会被总入口覆盖。private 根目录下的旧草稿仅用于追查规则修订，不应混入 private/final 的最终结果。程序未统计的病种不会被填入虚构患者。

疾病词典、指标别名和共享字段位于 definitions.py。原规划明确写出的常见病字段用于核对；罕见病的初步字段及痛风等扩展字段仅作为候选检查范围，不代表专病 Skill 已完整定义。按同一患者去重，但允许真实的多病共存。分型不清的糖尿病与普通高甘油三酯血症仅保留在辅助检索清单，不自动升级为特定病型。旧 NAFLD/NASH 作为独立补充组，不算作现代 MASLD 确诊。

field_aliases.py 保存本库实际使用的检验缩写扩展，包括 LDLcalc、LDLmeas、Triglyc 和 Cholest，并将 CHOL/HD 比值与总胆固醇区分。指标词典修订不改变已经选中的患者；其代码校验值另存于 extraction-summary.json。

初筛限定在既往病史与出院诊断。携带者、亲属患病、明确否定、疑似或筛查语境保守排除。罕见病在整份出院小结中的额外命中另存 SQLite 的 rare_fulltext_mentions 表，供扩大上下文人工检查；这些命中不自动进入确诊队列。零入组仅表示本套病名和语境规则未选出患者。换行、拼写、缩写、文书错误和诊断复制均会造成遗漏或误收，算法敏感度和特异度尚未独立测定。

指标提及、数值候选、阴性陈述、检查计划和比较阈值分别保存。每位患者、每个字段、每种状态最多保留两条不同摘录，所有匹配行另计总数。单位覆盖指保留摘录中的明确单位，未从常识补齐单位。文书日期仅作为文书日期保存，未冒充测量日期。未找到记录不能解释为正常或不需要检查。

出院药单及随访标题只说明相关段落存在。本轮尚未抽取完整药物剂量、依从性、测量设备、空腹状态、餐前餐后、检查完成日期和结构化人口学信息，也未生成指南阈值或治疗建议。年龄与妊娠适用性未独立核实，成人规则不能直接套用于整个样本。历史缓解、自述病史、糖尿病分型冲突和前期状态后续变化单独标记，仍需逐例解释。

查看本地抽样依据可以运行：

```bash
python3 review_candidates.py --run private/final --diseases t2d --limit 50
python3 review_candidates.py --run private/final --field hba1c --limit 20
python3 -m unittest -v test_audit.py
```

test_audit.py 使用合成文字测试分型、家族史、否定、携带者、疑似、指标目标值及不同标本。合成文字绝不计入真实患者数。源码可供团队审阅；患者资料、原始 MIMIC 文件和逐例摘录均不应随源码发布。
