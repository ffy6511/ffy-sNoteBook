---
{"dg-publish":true,"permalink":"/obsidian////chapter-1/","created":"2024-04-22T10:15:02.053+08:00","updated":"2024-09-08T15:25:05.504+08:00"}
---

# 1.命题逻辑
1. <mark style="background: #BBFABBA6;">非P的所有记法</mark>![Pasted image 20240422101804.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240422101804.png)
2. <mark style="background: #BBFABBA6;">逻辑运算符</mark>（联结词）
	1. Negation ¬ (NOT)
	2. Conjunction  $\wedge$ (AND)
	3. Disconjunction $\vee$(OR)
	4. Exclusive or (NOR)
		1. 
	5. <mark style="background: #FFB86CA6;">Conditional operator</mark> （if-then)  $p \rightarrow q$![Pasted image 20240422103501.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240422103501.png)
	6. Biconditional operator $p \leftrightarrow q$ 
		1. p if and only q
		2. 也写作 p iff q
	7. 补充：非或 NOR  $p \downarrow q$ 
		1. 与OR的情况相反
		2. 有1出0,仅当全0时出1
3. <mark style="background: #BBFABBA6;">优先级</mark>
	1. 括号最高
	2. 其次为，<mark style="background: #FFF3A3A6;">逆与或单双</mark>
4. <mark style="background: #BBFABBA6;">命题</mark> *proposition*
	A proposition is a declarative sentence that is either true or false, but not both.
# 2.命题逻辑的应用
- 检验系统一致性 Consistent
	列出真值表，检验是否存在底层变量的赋值方式使得整体为真
# 3.命题等价式
1. <mark style="background: #BBFABBA6;">基本概念</mark>
	1. Tautology 永真
	2. Clontradiction 永假
	3. Contingency 可能为真或假
2. <mark style="background: #BBFABBA6;">逻辑等价表</mark>
	![Pasted image 20240422104341.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240422104341.png)![Pasted image 20240422104435.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240422104435.png)
3. *Satisfiability* <mark style="background: #BBFABBA6;">可满足性</mark>
	1. A compound proposition is satisfiable if there is an assignment of truth values to its variables that make it true. 
	2. When no such assignments exist, the compound proposition is **unsatisfiable**.
#  4.谓词和量词
1. <mark style="background: #BBFABBA6;">基本概念</mark>
	1. Predicates 谓词
	2. Quantifiers 量词
2. <mark style="background: #BBFABBA6;">量词的分类</mark>
	1. 全称量词--任意
	2. 存在量词--存在
	3. Uniqueness quantifier--存在且仅存在一个![Pasted image 20240422110933.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240422110933.png)
3. <mark style="background: #BBFABBA6;">转为逻辑表达式的注意要点</mark>![Pasted image 20240422111154.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240422111154.png)
	区分:<mark style="background: #FFF3A3A6;">任意的蕴含</mark> 与 <mark style="background: #FFF3A3A6;">存在的合取</mark>
# 5.嵌套量词
>Two quantifiers are nested if one is within the scope of the other.
1. 量词类型带来的变化
	The <mark style="background: #FFF3A3A6;">order</mark> of nested quantifiers <mark style="background: #FFF3A3A6;">matters</mark> if quantifiers are of <mark style="background: #FFF3A3A6;">different types</mark>![Pasted image 20240422111407.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240422111407.png)![Pasted image 20240422111508.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240422111508.png)
## <mark style="background: #BBFABBA6;">子句</mark>
1. Disjunctive (Conjunctive) Clauses
2. 析取关系的逻辑表达式为析取子句
## <mark style="background: #BBFABBA6;"> 范式</mark>
1. 区分
	1. CNF 合取范式：（子句）先析取再合取![Pasted image 20240422111938.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240422111938.png)
	2. DNF 析取范式：（子句）先合取再析取![Pasted image 20240422111957.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240422111957.png)
	3. 单独的一个子句，可以认为同属于两者
		1. 析取子句看作合取范式的整体元素
	4. 最后的运算是xx，就是xx范式
2. 获得范式结构的方法
## <mark style="background: #BBFABBA6;">FDNF</mark>
>完全析取范式
- <mark style="background: #ADCCFFA6;">最小项</mark> *minterm*:变量出现<mark style="background: #FFF3A3A6;">且仅出现一次</mark>的<mark style="background: #FFF3A3A6;">合取</mark>子句
- 如果一个公式是 <mark style="background: #FFF3A3A6;">最小项的析取</mark>，那么就被称为~
- 举例：（p,q,r为元素）![Pasted image 20240422112446.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240422112446.png)
- 获得方式：
	1. 运用逻辑等价进行公式的变形
	2. 利用真值表，找出所有$F$为ture的赋值情况![Pasted image 20240422112602.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240422112602.png)
## <mark style="background: #BBFABBA6;">前束范式 PNF</mark>
>Prenex Normal Form
- 形式：![Pasted image 20240422112721.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240422112721.png)
- 结论：任何表达式均可化为PNF
- **转化的步骤**:
	1. 转换箭头![Pasted image 20240422112942.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240422112942.png)
	2. 去掉逆命题![Pasted image 20240422113002.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240422113002.png)
	3. 根据需要重命名变量（任意与存在冲突时）
	4. 将所有的逻辑变量前置![Pasted image 20240422113050.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240422113050.png)
- 化为 Prenex CNF and DNF
	1. 先化为PNF
	2. 将后面的逻辑表达式进一步化为CNF/DNF
# 6.推理规则
1. <mark style="background: #BBFABBA6;">步骤</mark>：
	1. 假设premises为true
	2. 运用逻辑等价关系得到结论为true
>在前提为真的情况下，结论为真，则称这个论证是有效的
2. <mark style="background: #BBFABBA6;">推理关系的表格</mark>![Pasted image 20240422114434.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240422114434.png)![Pasted image 20240422114458.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240422114458.png)
	<mark style="background: #FFB86CA6;">要求记住公式的名称，并规范书写！</mark>
3. 带有量词的推理公式![Pasted image 20240422113832.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240422113832.png)
	1. 全称指定 与 全称推广
4. 补充
	1. 全称三段论 UMP![Pasted image 20240422114557.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240422114557.png)
	2. 全称拒取 UMT![Pasted image 20240422114608.png](/img/user/obsidian/%E5%9B%BE%E7%89%87%E5%AF%84%E5%AD%98%E5%99%A8/Pasted%20image%2020240422114608.png)