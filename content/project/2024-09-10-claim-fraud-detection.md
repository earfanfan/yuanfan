---
title: 一种基于人寿保险理赔案件的团伙欺诈检测方法
author: yuanfan
date: 2024-09-10T20:36:45+0800
slug: claim fraud detection
categories:
  - R
tags:
  - R
draft: no
---

<script src="/rmarkdown-libs/htmlwidgets/htmlwidgets.js"></script>
<script src="/rmarkdown-libs/viz/viz.js"></script>
<link href="/rmarkdown-libs/DiagrammeR-styles/styles.css" rel="stylesheet" />
<script src="/rmarkdown-libs/grViz-binding/grViz.js"></script>

本文提出的这种方法在计算逻辑上非常简单，但是在业务逻辑上稍微有些复杂。总地来说，这是一种人人都能想得到的方法，但键者在走了许多弯路以后，选择了它并将其耐心打磨成型。

<!--more-->

保险公司的利润来源通常是死差损、费差损、利差损，因而保持多差少损需要依靠严格的风险控制手段，其中在控制客户带来的风险方面主要集中于“核保”和“核赔”这两个环节。在客户向保险公司投保后至保险公司决定承保前，投保单需要通过“核保”流程才能成为正常生效的保单。而“核保”所做的主要有两点：其一，进行风险评估，根据客户提交的资料进行审核、分类，无风险的判定正常通过，风险较小的有条件通过，条件通常是附加特别约定、限制最高投保额度、对次标体/职业/残疾等因素调整加费等等，风险较大的拒绝通过；其二，识别逆选择风险，有些客户投保时会隐瞒信息，比如带病投保，保险公司仅凭借投保材料难以识别风险，一般需要通过第三方机构获取客户过往真实病史信息来辅助决策。由于实际业务中“核保”并不能做到百分百控制风险，依然会有风险较大的客户正常承保后伪造出险材料然后向保险公司申请理赔，因而“核赔”流程中也需要评估风险。

但是“核保”和“核赔”在评估风险的目的、面对的困难、使用的手段上均有本质区别，前者侧重于控制风险，对可能存在的风险做出不同的决策，给出的复杂决策本身会进一步降低保险公司承担风险的成本，而后者是在已经出险的情况下进行审核或调查，目的是要尽可能挽回损失，能做的决定只有赔、少赔或者不赔，许多时候即便怀疑是保险欺诈，也很难有确切证据证明。

保险金欺诈按参与作案人数多寡可分为个人作案和团伙作案，个人的欺诈检测类似于异常检测，非常依赖核赔业务人员提供的经验规则，而团伙的欺诈检测难度更大，其面临的难点主要有以下几点。

1.  保险公司与欺诈团伙之间信息不对称，而且保险公司之间、保险公司与医疗机构之间的信息共享也并不充分，欺诈行为往往隐匿于种种因素造成的信息差。

2.  绝大多数欺诈团伙的案件之中会同时存在共同点和差异点，过于追求寻找共同点反而更容易忽略差异点，导致误判。

3.  欺诈团伙的作案手法一直在更新，保险公司仅能根据历史案例的特点防止同一团伙再度作案，很难预防未来出现新的欺诈手段。

4.  欺诈检测方法只能提出可疑点，需要依靠调查来取证，通常很难取得足够完整的证据来判定欺诈行为，因此在验证方法效果时也难以评估能起多少作用[^1]。

# 一、方法简介

基于保险理赔的团伙欺诈检测通常有以下思路，这些也都是走过的弯路。

第一种，先聚类，如果某一个类中存在欺诈案件，则此类均可被视作可疑团伙。走不通的原因有这些：其一，常见的基于距离或密度的聚类算法所适用的数据类型都是数值型，而实际理赔业务中的数据类型非常复杂，除了数值型，还有日期型、类别型（类别成千上万的单个字符串或逗号拼接的多个字符串）、文本型（短文本、长文本），且各类型数据转换为用数值表达的特征后，各特征在业务逻辑上的重要性并不相同，这点与一些基础的聚类算法逻辑上是互相违背的；其二，欺诈团伙本身在人与人之间的关联程度非常弱，社区检测（community detection）一类的网络聚类算法并不普遍适用，仅适用于检测有亲属间关系的欺诈团伙。

第二种，基于不同团伙特点的异常检测，走不通的原因是，根据历史欺诈案件能总结出与整体不一样的异常特征，换个地域或者换一群人，那些“不一样”不一定仍然算异常，很多就是正常的。

第三种，总结出所有可能存在异常特征的方向，然后对可疑案件逐级扫描，比如一些明显异常的特征（同一手机号、收据号被不同人使用）、异地投保、就诊方式异常（不常见的住院）、极短期出险、医疗费用异常等等，随后在大方向之下继续逐层级寻找异常，以此来找出新的目标案件中的具体异常特征。这样也走不通的原因是，虽然那些方向下许多特征可能存在异常，但并不能以明确的标准去断定确实存在异常。也与上一种方法存在同样的缺陷，不一样确实可疑，但不一样不等于有风险。

在持续经历过以上三种失败后，最终得到一个新的思路：欺诈团伙留下的信息往往是共同点与差异点并存，单独找相似或者单独找异常都走不通，在可投入的人力物力有限的情形下，根据可疑的目标案件去找相似才是最可行的。

那么主要应用场景是这样的：已知一个或两个有可疑的目标案件，需要从同一立案责任下的所有其他案件中找出最相似的少数几个案件。由于欺诈团伙具有比例极低（仅占理赔案件十万分之一）、作案手法多变（无法用相对较少的特征来描述其行为）等特点，在保险公司所获信息不充分的前提下，欺诈团伙的异常行为特征并不突出且变换多端，因此各类通用的机器学习算法如聚类、分类、回归、异常检测等不能直接迁移应用于这个场景，所以团伙欺诈检测的重点放在判定可疑的相似。

综上，本文提出的欺诈检测方法主要针对的是团伙作案，所应用的场景仅限于已经知晓一个或两个可疑的案件，在此基础上检测出更多相似案件。并且此方法的各类细节仅适用于人寿保险，不涉及财产保险。

本方法的基本思路如下图所示：假设每个案件都有近60个基础特征（客户与保险公司由业务接触留下的基础信息），按照这些基础特征来计算与目标案件之间的距离，由于这些基础特征的重要性在业务逻辑上差别极大，若直接从特征的距离汇总到案件的相似度，会导致重要性极低的特征反而对结果造成更大影响，因此要先按不同业务属性汇总距离，然后才汇总为案件相似度，最后经过变点检测得到与目标最相似的案件。

其中，在一个目标的情况下，特征的重要性要根据业务经验直接选定，即直接根据业务逻辑选出需要增加权重的基础特征，具体的权重系数则由进一步的数据分析试验结果来确定。在两个目标的情况，仅根据业务经验来指定一些筛选重要特征的规则，具体的筛选结果由数据运行后得出，而具体的权重系数也由反复的数据分析试验结果来确定。

<div class="grViz html-widget html-fill-item-overflow-hidden html-fill-item" id="htmlwidget-1" style="width:672px;height:480px;"></div>
<script type="application/json" data-for="htmlwidget-1">{"x":{"diagram":"digraph{\n # 定义图形布局，从右至左\n  graph[rankdir = TB]\n # 定义节点\n  node[shape = rectangle]\n      S[label = \"案件相似度\"]\n      A1[label = \"案件属性\"]\n      A2[label = \"医疗属性\"]\n      A3[label = \"客户属性\"]\n      A4[label = \"投保属性\"]\n      F1[label = \"特征1\"]\n      F2[label = \"...\"]\n      F3[label = \"特征20\"]\n      F4[label = \"特征21\"]\n      F5[label = \"...\"]\n      F6[label = \"特征30\"]\n      F7[label = \"特征31\"]\n      F8[label = \"...\"]\n      F9[label = \"特征49\"]\n      F10[label = \"特征50\"]\n      F11[label = \"...\"]\n      F12[label = \"特征60\"]\n      R[label = \"最终结果\"]\n # 定义线\n M1[shape = point, width = 0.01, height = 0.01]\n     {A1,A2,A3,A4} -> M1[dir = none]\n      M1 -> S\n M2[shape = point, width = 0.01, height = 0.01]\n     {F1,F2,F3} -> M2[dir = none]\n     M2 -> A1\n M3[shape = point, width = 0.01, height = 0.01]\n     {F4,F5,F6} -> M3[dir = none]\n     M3-> A2\n M4[shape = point, width = 0.01, height = 0.01]\n     {F7,F8,F9} -> M4[dir = none]\n     M4 -> A3\n M5[shape = point, width = 0.01, height = 0.01]\n     {F10,F11,F12} -> M5[dir = none]\n     M5 -> A4\n S -> R[label=\"排序，变点检测\"]     \n}","config":{"engine":"dot","options":null}},"evals":[],"jsHooks":[]}</script>

# 二、一个目标的方法细节

这个方法的基本步骤是：

1.  准备好所有案件的基础特征数据。
2.  输入一个目标案件，选择该案件的一个立案责任作为目标立案责任。
3.  根据目标立案责任按照指定规则筛选出同一立案责任下的待匹配案件。
4.  计算目标案件与所有待匹配案件在每一个基础特征下的距离，并汇总成最终的案件相似度。
5.  将案件相似度从小到大排序，做变点检测，变点所在序号及以上的案件即为目标案件的相似案件。

## 2.1. 保险公司拥有的信息

当一个客户向保险公司投保，等到出险理赔时将会留下四种维度的信息，分别是客户维度、保单维度、险种维度、案件维度，下面分别展开介绍保险公司拥有的基本信息。

- 客户

  - 五项基本信息：姓名、性别、出生日期、证件号、证件类型。
  - 其他信息：联系方式、联系地址、职业、在保险公司的身份等。

- 保单

  - 客户身份：在一个保单中通常有三种客户身份，即投保人、被保人、受益人。如果是个人保单，投保人会是一个自然人。如果是团体保单，投保人会是一个非自然人，即投保单位。一个投保人可以为多个被保人投保，也可以指定多个受益人。
  - 渠道与代理人：保险公司会通过多种渠道售卖保单，较为基础的划分方式会是为个险、团险、银行代理，每种渠道由代理人与客户进行接触。各渠道依据自行定义的基本法来管理代理人及其所属组织信息。

- 险种

  - 险种类别：险种是指客户投保时选定的具体保险产品，依据产品类别可划分为人寿保险、健康保险、意外伤害保险，其中健康保险又可进一步划分为疾病保险、医疗保险、意外医疗保险、护理保险等多种产品类型。一个保单中可以投保多个险种。
  - 险种责任：每一款保险产品通常有多种不同的可选责任，到了理赔环节，赔付多少的依据就是责任判定的结果。

- 案件

  - 事故：被保险人出险后向保险公司报案，后者会根据事故情况立案，每个理赔案件对应一个事故者，但是可以包含多张保单多个险种。案件中需要记录事故发生的日期、事故经过、事故性质、事故者现状、事故名称（ICD10）等信息。
  - 责任：事故者出险通常分为疾病、意外两种事故类型，其结果又分为死亡、伤残、医疗、重疾等几种，那么组合起来会得到多个不同的立案责任，即疾病死亡、意外死亡、疾病伤残、意外伤残、疾病医疗、意外医疗、疾病重疾、意外重疾等。实际业务中一个案件可以选择多个立案责任，各立案责任还会细分出数百种保险责任细项。
  - 医疗：绝大多数涉及人的生命健康的理赔案件都需要记录医疗信息，包括医院名称、医院所属省市区、总账单金额、门诊账单金额、住院账单金额、住院天数、入院日期、出院日期、收据号等。

将以上各类信息汇总为案件维度，可以得到每个案件的基础特征信息。

## 2.2. 计算案件相似度

### 2.2.1. 单个特征的距离计算

按照案件基础特征的数据类型分为文本类、数值类、日期类，由于许多特征的取值都有特别含义，需要依托实际业务含义来处理，因而要单独划分一个规则类，随后分别对四种类型的特征逐个计算距离。

- 文本类

  - 第一种：基于统计学的计算方法，比如计算姓名之间的距离可以计算重叠字数，医院名称在分词后计算有交集的词语数量以及对第一个词增加权重。
  - 第二种：基于语义理解的计算方法，比如地址本身有层次结构关系，对于分词结果如省、市、区不能作为相互独立的词义来理解，可以赋予不同权重。
  - 第三类：基于模型的计算方法，比如用结巴分词提供的 SimHash 算法来计算文本相似度，得到如事故经过这类长文本的特征的距离。

- 数值类

  - 第一种：数值相减，比如计算年龄之间的距离可以取相减后的绝对值。
  - 第二种：分类处理，根据业务需要将住院天数、账单金额、日均金额等特征合而为一，当账单金额和日均账单金额都不为空时，需要在同一 ICD10小组内计算两组金额的欧式距离；当日均账单金额为空账单金额不为空时，计算账单金额的距离；当账单总金额缺失但住院天数不为空时，计算天数的距离；当账单总金额、住院天数均缺失时，距离置为最大值。

- 日期类

  - 第一种：日期相减。
  - 第二种：拆分年、月、日，比较这三项数字之间的距离。
  - 第三种：以上两种方法分别计算后合并。

- 规则类

  - 第一种：判断是否一致。
  - 第二种：判断有无交集。
  - 第三种：依各个特征的特点定义规则。比如医院所属省市，不同省份、同省不同市、同省同市分别指定距离。又如身份证号、职业代码，前2位、前4位、前6位相同时分别指定距离。再如身故日期与理赔申请日期之间的天数，依7天以内、7-10天、2月以内、3月以内、3月以上等分别指定距离。

特征的缺失值要做特别处理，所有特征的距离计算结果要统一做归一化处理，使距离的范围在0到1之间。

### 2.2.2. 结果汇总

所有特征被划分为四种属性，分别是案件属性、医疗属性、客户属性、投保属性。因此汇总结果的步骤依次是：`单个特征的距离-->四种属性的距离-->案件相似度`

将单个特征的距离分别汇总为四种属性的距离时，需注意在不同情况下计入不同的特征。

- 不同立案责任下案件属性中计入不同特征：立案责任含死亡时，计入身故日期；立案责任含意外时，计入意外事故原因；立案责任含伤残时，计入残疾代码和伤残鉴定日期；案件有入住院日期时，不计入事故日期等，避免重复的日期放大日期的影响。

- 客户特点不同时客户属性中计入不同特征：被保人出险时年龄大于等于18岁且投被保人不一致时，计入所有投保人、被保人特征；被保人出险时年龄大于等于18岁且投被保人一致时，投保人、被保人特征不需重复计入，只选一类；被保人出险时年龄小于18岁时，被保人的身份、职业、住址、手机号、邮箱等多数为空，不必计入。

汇总的方法如果是加权平均，那么根据业务需要对选择的特征或属性增加权重。

## 2.3. 变点检测

选择最终输出结果时运用的是一种简单的变点检测方法，这里只是结合均值平移、标准差变化写了一个贴合业务的算法。

1.  对所有待匹配案件的案件相似度按升序排列，取一阶差分。
2.  从序号2开始循环计算，当一阶差分值大于均值加标准差乘以倍数时，输出序号。倍数的取值顺序为3-2-1。只有当得到的序号大于20时才返回。
3.  如果第一个差分值比接下来19个差分值都大，返回1。
4.  以上结果都没有返回时，返回10。

此算法的 R 代码如下：

``` r
first_diff <- function(values) {
  differences <- diff(values)
  mean_diff <- cumsum(differences) / (1:length(differences))
  sd_diff <-
    sqrt(cumsum((differences - mean_diff) ^ 2) / (1:length(differences)))
  
  result <- 10  # 默认返回值
  
  for (threshold in c(3, 2, 1)) {
    for (i in 2:(length(differences) - 1)) {
      if (differences[i] > mean_diff[i] + threshold * sd_diff[i]) {
        if (i < 20) {
          result <- i  # 存储返回值，而不是直接返回
          break
        }
      }
    }
  }
  
  # 如果第一个差分值比接下来19个差分值都大，返回1
  if (is.na(i) == FALSE & differences[1] > max(differences[2:20])) {
    return(1)
  }
  return(result)  # 返回存储的值
}
```

# 三、两个目标的方法细节

相比仅知晓一个目标案件，已经知晓两个目标案件有可能是欺诈团伙时，可以更有针对性地找出团伙中的共同异常点。两个目标的方法细节与一个目标的大体类似，区别在于一个目标时所需增加权重的特征或属性人为指定，而两个目标时所需增加权重的特征通过两个目标之间的共同异常行为来判断。

这个方法的基本步骤是：

1.  准备好所有案件的基础特征数据。
2.  输入两个目标案件，判断两个案件有无相同的立案责任，若有则选择一个作为目标立案责任。
3.  根据目标立案责任按照指定规则筛选出同一责任下的待匹配案件。
4.  筛选需要加权重的特征。
5.  分别计算两个目标案件与待匹配案件在每一个基础特征下的距离，根据上一步筛选的结果增加权重后汇总出案件相似度。
6.  根据上一步的结果，结合符合业务需要的规则，组合出最终结果。

## 3.1. 筛选需要加权的特征

- 第一种，判断两个目标案件是否存在一致的异常行为。
  - 如果两个目标案件存在可疑的住院方式的特点，比如两个目标的 ICD10小组相同，所有案件中该 ICD10小组大多为门诊，而两个目标案件均住院，这是不常见的住院行为，那么筛选出相关特征。
  - 如果两个目标案件存在可疑的异地投保行为，那么筛选出相关特征。
  - 如果两个目标案件存在可疑的组织特点，比如职业类别中都含有医院，投被保人身份都很特殊，那么筛选出相关特征。
  - 如果两个目标案件存在可疑的家庭特点，比如案件之间的投保人、被保人、身故受益人、领款人等信息有交集，那么筛选出相关特征。
  - …未能详尽列举的其他异常行为。
- 第二种，判断两个目标案件的单个特征的取值内容在整体中是否占比较小，在整体中显得异于寻常。
  - 步骤1：做探索性数据分析，去掉取值内容本来的类别就很少的特征，避免干扰。
  - 步骤2：在剩下的特征中选出两个目标取值一致或有交集的特征。
  - 步骤3：筛选出那些取值在整体中占比较小的特征。比如特征 F1的取值范围有 a/b/c/d/e 等五个，两个目标案件的特征 F1取值均为 b，而在所有待匹配案件中 F1 取值为 b的比例非最大，那么选出特征 F1。
- 第三种，基于业务需要，直接选定部分特征。

## 3.2. 组合最终结果

在分别得到所有待匹配案件与两个目标案件的案件相似度后，两份结果要组合出最终结果。

- 第一种，按业务需要的方式组合

  - 入选原因一：单一目标案件的变点检测结果。
  - 入选原因二：两个目标案件相似度前20中存在重复的案件。
  - 入选原因三：若两个目标案件均存在异常行为，那么在案件相似度前20中存在相同异常行为的均需入选。
  - 入选原因四：若两个目标案件的投保人、被保人和身故受益人没有交集，但领款人相同，那么待匹配案件中同一领款人的案件均需入选
  - …未列举的其他入选原因。

- 第二种，运用统计学的方法将两份结果汇总为一个综合相似度，然后再做变点检测，筛选最相似的案件。

# 四、效果评估

许多机器学习算法都需要使用相关评估指标来验证效果如何，选择合适的评估指标是为了提升使用效果。本方法使用以下方式来评估最终效果。

- 第一种，借用二分类的评估指标——准确率和召回率，即输入一个或两个目标案件以尽可能少的成本、尽可能全地召回已知的欺诈案件。

- 第二种，实际的业务使用场景中往往是先有一个目标，匹配出一些相似案件后，再挑选两个目标继续匹配，因此根据历史欺诈团伙案件的具体情况来具体分析，究竟哪些案件与目标更相似，哪些案件没有检测出是可以接受的。

# 五、总结与展望

鉴于保险理赔案件的团伙欺诈检测面临诸多难点，本文提出的方法将应用场景限定在已存在可疑案件的情况下，即已知一个或两个可疑的目标案件，匹配更多相似案件。

本方法的特点有这些：其一，使用传统的机器学习算法构建模型的本质是用历史数据预测未来，也就是要寻找历史数据中的“确定性”，预测未来现实中的“不确定性”，建立团伙欺诈检测模型时寻找“确定性”等于寻找异常特征，不能够找全所有欺诈团伙的异常特征就决定了模型的上限有限，因而本方法跳出这个思路，转而由“确定性”的可疑案件来匹配更多“不确定性”的相似案件；其二，本方法在计算案件之间的距离时不构建行为特征，但基于历史经验总结的可能会出现异常的几种方向，通过这些方向是否出现异常来确定需要增加权重的基础特征。

这个方法有这几点不足：其一，运行时效慢，尚且不能够运用到实时计算的业务场景中，数据量小的时候执行一次几十秒，数据量大的时候执行一次要1到2分钟；其二，内部数据有限，使得模型的洞察能力有限，本方法在一个目标的应用场景下是人为指定四种属性的权重，对选择哪些特征或属性加权重所运用的是更加平衡的策略，如果有的欺诈团伙在客户属性和医疗属性上更相似，但人为划分的是对客户属性和投保属性赋予更大的权重，那么最终结果中不可避免会混入与目标投保属性更相似的案件；其三，所使用的自然语言处理技术的语义理解能力受限，使得模型对文本的理解能力有限，本方法使用的自然语言处理技术仅限于分词工具和文本相似度算法，遇到比如姓名、地址这类包含人类社会常识的文本时不能准确理解语义，所以模型在处理文本时的理解能力也不足。

现今保险欺诈的行为无外乎虚构保险标的、夸大损失程度、编造虚假的事故原因或编造未曾发生的事故，要想实现这些目的，欺诈的手段总是随着反欺诈的手段而“进步”。在理赔反欺诈这项工作上，“矛”与“盾”的作用总是随时间推进而交错发生，即使保险公司和医疗机构不断地完善反欺诈的手段，欺诈团伙也总是能不断钻到新的漏洞。比如当欺诈团伙与业务员有关时，如果原来同一业务员名下客户病种集中度较高代表风险高，那么一旦针对此特点的反欺诈手段起到防范作用，更远的未来，业务员还可以唆使名下客户特意分散病种。又比如以前医疗报销使用的是纸质票据，欺诈团伙可以通过修改或伪造票据来套利，当医疗机构统一推行电子票据后，欺诈团伙又会真住院但采取多家投保报销的方式获利。又比如，病情诊断依赖医院的检查指标，但如果有医护人员参与欺诈行为，不一定非得改指标结果，比如一些抽血化验类的检查，欺诈团伙只需要想办法影响样本，也会影响最终的检查结果。

如果允许展望的话，从保险公司的角度来看，信息不对称才是导致反欺诈工作做起来很困难的最大原因。事实上，所有保险公司的承保、理赔数据都会按监管要求报送给中国银保信，要是医保系统的数据也能一块整合起来，这些数据能够发挥更大作用的话，那么保险公司的反欺诈、医疗机构的反欺诈都会更容易[^2]。

[^1]: 虽然理赔流程需要运用审核、调查等手段来防范风险，但同时理赔业务也是一种面向客户的服务，随着保险行业竞争加剧，各保险公司在理赔流程上设定了严格的时效标准，甚至纷纷推出直赔、快赔、预赔等服务，因而欺诈检测步骤往往滞后，更加难以判定究竟起到了什么效果。

[^2]: 这篇文章是从反欺诈的角度写的，人的信息更透明，自然更便于管理，但换个角度想，所有信息整合到一起也容易产生新问题，如果信息差从分散的个人挪到了掌握数据的机构手里，垄断了数据的机构将会垄断某种程度上的话语权、定价权之类的权力。