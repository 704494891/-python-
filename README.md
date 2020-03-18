#  大五人格测试问卷答题系统python版

##  介绍

**大五是心理学家在对人格进行因素分析时，发现人格的基本结构是由“五大”因素构成的，五大人格，是目前最为流行的人格结构模型，而且在实践也得到了广泛良好的应用。大五人格问卷的结构分别测试五个大的维度，每个大的维度下面还有六个小的量表,如下所示**
* N：神经质
	* N1焦虑，N2愤怒敌意，N3抑郁，N4自我意识，N5冲动性，N6脆弱性
* E:外向性
	* E1热情性，E2乐群性；E3自我肯定，E4活跃性，E5寻求刺激，E6积极情感
* O：开放性
	* O1想象力，O2艺术美感，O3情绪体验性，O4行动，O5观念，O6价值
* A：宜人性
	* Al人际信任，A2坦诚，A3利他性，A4顺从性，A5谦虚，A6温存
* C:严谨性
	* C1胜任感，C2计划条理性，C3责任感，C4事业心，C5自律性，C6审慎胜

**本项目是为大五人格测试题编写的一个答题软件，测试题分为5大维度，每个维度的次级维度都有一定数量的题目对应，整个问卷有240道题，答题者需要使用数字1～5对每个问题进行作答，数据越大越符合描述。最后软件会给出每个大维度和其下属各个小维度的分数，答题者需要依靠分数去对照`result.docx`中相应的文字表述。**

##  使用说明

-  用命令窗口进入`main.py`所在文件夹，并在其中输入`python main.py` 进行答题。 *(每次输入一个答案，按回车键进行下一个题，且答案只能输入1~5的数字)*
-  在答完题后结果会将各个大维度和小维度的分数对应显示出来，根据各个维度的分数去 `result。docx` 文件中找对应的文字表述,得分1、2、3为低分，4、5、6、7、8、9、10为高分。
-  如果要增加和删减题目请在`text-1`文件夹下增加题目内容，并将其索引填入对应的文件夹。
 
##  环境依赖

- `python3`

##  文件说明

1. `main.py` : 主函数

2. `functions.py` : 功能模块

3. `all-index` : 各个维度下题目的索引

4. `re-index` : 得分反向扣除的题目索引

5. `text-1` : 题目信息

6. `result` : 得分结果所对应的文字表述

##  各功能模块的作用

1. `show_question` 展示问题并保存输入的答案

2. `Judgement_input` 判断输入的分数是否是正确的数字

3. `alculate_reverse_score` 把反向扣分的问题所对应的得分取反

4. `grade_covdict`  分数转化为字典格式{key=index：value=grades}

5. `slip_sum_grades` 得到各小维度分数之和

6. `add_all_grades` 将大维度的分数加入结果

7. `calculation_really_grades` 根据计算法则得出最后的分数*(具体计算法则会在下一节讲)*

8. `print_grades` 输出分数

##  分数计算法则
***说明：***每个大维度和其下所有的小维度都有各自的平均分和标准差，每个维度的最终得分都要根据其由表1查到的平均分和标准差带入表2计算得出。

**表1**

|维度代码|平均分|标准差|
| --- | :-----:  | :-----: |
|N|	83.78|	24.41|
|E|	109.96|	18.27|
|O|	110.64|	15.88|
|A|	113|	14.9|
|C|	123.88|	20.32|
|N1|	14.15|	5.7|
|N2|	13.82|	5.24|
|N3|	14.37|	5.7|
|N4|	15.35|	4.73|
|N5|	14.86|	4.88|
|N6|	11.23|	5.09|
|E1|	21.53|	4.27|
|E2|	18.69|	4.65|
|E3|	15.1|	4.37|
|E4|	18.33|	4.74|
|E5|	17.24|	4.64|
|E6|	19.07|	4.85|
|O1|	15.19|	4.19|
|O2|	20.7|	4.88|
|O3|	19.47|	3.95|
|O4|	15.02|	3.61|
|O5|	19.62|	4.98|
|O6|	20.64|	3.97|
|A1|	21.07|	3.94|
|A2|	19.03|	5.11|
|A3|	20.99|	3.53|
|A4|	15.33|	4.64|
|A5|	16.67|	4.06|
|A6|	19.91|	3.59|
|C1|	20.8|	4.34|
|C2|	18.39|	4.21|
|C3|	23.47|	4.22|
|C4|	20.02|	4.34|
|C5|	20.48|	4.66|
|C6|	20.72|	4.63|

**表2**

|得分|原始分分数段|
| :---: | :-------------: |
|1|	X＜M-2SD|
|2|	M-2SD≤X≤M-1.5SD|
|3|	M-1.5SD＜X≤M-SD|
|4|	M-SD＜X≤M-0.5SD|
|5|	M-0.5SD＜X≤M|
|6|	M＜X≤M+0.3SD|
|7|	M+0.3SD＜X≤M+0.6SD|
|8|	M+0.6SD＜X≤M+SD|
|9|	M+SD＜X≤M+1.5SD|
|10|	X＞M+1.5SD|
 
 ***备注：X为每个受测者在每个因素的得分，M为各因素的平均数，SD为各因素的标准差。***
   

