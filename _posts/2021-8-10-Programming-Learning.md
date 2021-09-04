## 修炼之道
### 4.3.5 隐喻
“隐喻”：语言和意象共同的地基，是在左右脑半球之间，在潜意识和意识之间来回游戈的途径。

隐喻作为艺术的常见现象，编程本身是一项艺术，所以隐喻在编程这项活动中是存在的，编程活动前的活动内容属于其他领域，计算机是图灵提出的计算机模型（借鉴了记忆模型）产生的，所以计算机具有递归循环特性，计算机这种东西算是哪方面的产物，艺术or科学？说实话计算机是人**为了偷懒**而突然想到的东西，它能够做到人做不到的事情，应该算进大自然的产物里去（**大自然的研究-->生物方向**）。动物文明从会使用资源工具开始，如果动物会造工具，那一类动物的群体就自形成一个子系统。计算机（Lambda演算模型）也会造工具，那么计算机模型自形成一个子系统，这些子系统都有一个共同特征：**循环（衔尾蛇、永恒）、自主性**。

循环特征是我们人类赋予它的，[计算机科学](https://book.douban.com/review/9404414/)主要**研究信息的存储、转化、表示**。编程活动前的其他领域不一定要使用计算机，也可以直接用数学公式来求解，**计算机局限在于它并不能证明还未证明的自然原理**。

物理、艺术（研究本身不需要形式语言/符号）是追求真理规律方面的，而数学、数理逻辑所涉及的符号是重用性、控制、使用方面的。  
但是你要把真理规律用到计算机这个载体里面，就需要形式语言/符号。（还要存放到计算机里面，人都给你锤爆）

交给你了，举一反三（逻辑延伸）。

空间的规律是对称，时间的规律是重复。

Tip：使用隐喻作为L型和R型相融之所。

一个字母表(alphabet)是一个非空有限集合, 该集合中的元素称为符号(symbol).

一个字母表$\Sigma$上的语言(language)是$\Sigma$中的元素构成的有限序列(称为串, 即string)的集合.

例如字母表$\Sigma=\{0,1\}$, 则我们可以定义一个$\Sigma$上的语言$L=\{x_1x_2\cdots x_n|\text{如果}x_i= 0,则x_{i+1}= 0\}$, 则该语言为
$$
L=\{\varepsilon, 0,1,10,11,100,110,111,\cdots\}
$$
即所有的$1$都出现在任何$0$之前的串. 其中, $\varepsilon$表示空串, 即长度为$0$的串.

我们说”序列”就要考虑顺序, 即$001$和$100$是不同的串.
串可以是空串, 即长度为$0$的串, 空串通常记作$\varepsilon$.

设$\Sigma$是一个字母表, $\Sigma^0=\{\varepsilon\}$表示空串的集合, $\Sigma^n=\Sigma\times \Sigma\times\cdots\times \Sigma$为$n$个$\Sigma$的直积. 则$\Sigma$上的一个语言定义为$\Sigma^\ast=\bigcup\limits_{i\in\mathbb{N}}\Sigma^i$的子集.

例如, 一个语言可以用来表示所有的有向无环图, 我们试图用字母表$\Sigma=\{0,1\}$上的语言来对图进行编码. 首先我们需要表示图$G=(V,E)$中的$V$, 我们约定$\dagger$之前的部分表示图中每个点的名称的长度$v$, 而$\dagger$之后依次的每个长度为$v$的连续子串表示图所有点的名称. 在所有的名称后, 我们用另一个$\dagger$作为分割, 其后依次的每个长度为$2v$子串表示一条有向边. 所有的有向边后以$\ddagger$结束.

$$
100\dagger0010\cdot0011\cdot0101\cdot0111\cdot1000\cdot1001\cdot1010\cdot1010\cdot1011\dagger\\0011\to1000\cdot0011\to1010\cdot0011\to1010\cdot0101\to1011\cdot\\0111\to1000\cdot0111\to1011\cdot 1000\to1001\cdot1011\to0010\cdot\\10011\to1010\ddagger
$$

$$
0\to01,1\to10,\dagger\to00,\ddagger\to11,\cdot\to\varepsilon
$$

### 判定问题
计算理论中最简单的问题, 就是判定问题, 即只能用$\text{YES},\text{NO}$回答的问题. 这类问题非常普遍, 例如问某个有向图是不是有向无环图, 那么这个问题的算法, 实际上是建立了一个映射. 如果用$L_{G}$表示所有的有向图构成的语言, 并用$0,1$分别表示$\text{YES},\text{NO}$, 那么这个问题实际上就是建立了一个映射$f:\{0,1\}^\ast\to \{0,1\}$, 且$f(x)=1$当且仅当$x\in L_G$. 而解决这个问题算法就是能够计算函数$f$的算法.

计算问题$f:(x,y)\mapsto x+y$可以转换为判定问题$g:\{(x,y,z)|x,y,z\in\mathbb{Z}_+\}\to\{0,1\}$, 其中$g(x,y,z)=1$当且仅当$x+y=z$, 即判定$z$是否为$x$和$y$的和的问题.

一个有限状态机是一个五元组$(Q,\Sigma,\delta,q_0,F)$, 其中

$Q$是一个有限集, 称为状态集  
$\Sigma$是一个有限集, 称为字母表  
$\delta:Q\times\Sigma \to Q$称为转移函数  
$q_0\in Q$是起始状态  
$F\subseteq Q$是接受状态集  

例如$q_2\overset{0,1}{\longrightarrow}q_3$表示映射$(q_2,0)\mapsto q_3$和$(q_2,1)\mapsto q_3$两条映射

从上面有关于自动机的描述, 我们可以看到, 当自动机$M=(Q,\Sigma,\delta,q_0,F)$处于起始状态$q_0$时, 我们输入一个$\Sigma$上的串$x\in\Sigma^\ast$, $M$会依次读取串$x$上的符号, 并根据状态机作相应的状态转换. 当整个串$x$读取完毕后, $M$可能处于某个接受状态$q\in F$, 也可能处于某个非接受状态$q^\prime\notin F$. 如果一个串$x\in \Sigma^\ast$使$M$按照上述运行方式运行后, 处于某个接受状态, 就记$M(x)=1$并称$M$接受串$x$, 否则记$M(x)0=$并称$M$拒绝串$x$.

我们可以发现, 自动机$M$根据上述运行的方式, 可以表示一个映射$f: \Sigma^\ast\to\{0,1\}$满足$f(x)=1$当且仅当$M(x)=1$. 如果一个语言$L$和一个自动机$M$满足$x\in L$当且仅当$M(x)=1$我们就说$M$识别(recognize)$L$或判定(decide).

$$
\textsf{REG}=\{L|\exists\text{自动机}M: x\in L\iff M(x)\}
$$

 $L=\{所有包含”001”串\}\in \textsf{REG}$

 设$L_1$与$L_2$均为语言, 定义它们之间的三种运算:
$$
L_1\circ L_2 = \{x_1x_2|x_1\in L_1, x_2\in L_2\}
$$
即$L_1\circ L_2$是所有$L_1$中的串与$L_2$中的串拼接构成的串的集合, 在不产生歧义的时候, 这个圈可以不写. 根据concatenation的翻译, 我们可以称该运算为”串联”.
$$
L_1\cup L_2 = \{x|x\in L_1 或 x\in L_2\}
$$
它所表示的意义和集合的并集一样.

而$L_1^\ast$表示的是由$L_1$中的任意串重复任意次(如果重复$0$次就得到$\varepsilon$)所得到的所有的串构成的集合. 例如$L_1=\{00, 01\}$, 那么$\varepsilon,00,01,0000,0101,000000,010101$等都是$L_1^\ast$的元素. 如果读者更倾向于形式化的定义, 那么$L_1^\ast$可以定义为

$$
L^0=\{\varepsilon\}, \quad L^n=\{x^n|x\in L\} \\
L^\ast= \bigcup_{i\in\mathbb{N}} L^i
$$

一个语言$L$是正则语言, 如果它满足以下命题之一

$L=\{a\}$, 其中$a$是某个字母表$\Sigma$上的符号;  
$L=\{\varepsilon\}$;  
$L=\emptyset$;  
$L=L_1\cup L_2$, 其中$L_1$和$L_2$均为正则语言;  
$L=L_1\circ L_2$, 其中$L_1$和$L_2$均为正则语言;  
$L=L_1^\ast$, 其中$L_1$为正则语言;  

空集也可以参与, 并且有:

空集与任何语言作$\circ$或$\cup$运算得到的都是空集
$\emptyset^\ast=\{\varepsilon\}$

描述一个正则语言的, 它由字母表种的符号, $\cup$运算符, $\circ$运算符, $^\ast$运算符还有括号组成. 我们可以用这些符号连同括号的组合来表示一个正则语言, 同样的, 这里的$\circ$在不产生歧义的情况下也可以略去不写.

例如, 正则表达式$R = (0\circ(0\cup 1))^\ast$, 表示语言
$$
L=\{\varepsilon, 00, 01, 0000, 0100, 0101, \cdots\}
$$
即所有长度为偶数且$1$只出现在从左至右第偶数位的串. 它的原理很简单, 它由长度为2单元$0\circ (0\cup 1)$重复任意次组成, 而在一以个单元种, 第一位必须是0, 第二位可以是1或0. 实际上这个语言确实是正则语言, 令$L_0=\{0\}, L_1=\{1\}$, 那么有
$$
L= (L_0\circ (L_0\cup L_1))^\ast
$$

**定义** 正则表达式

一个表达式$R$为正则表达式, 如果它是以下几种表达式之一

$a$, 其中$a$是字母表$\Sigma$中的一个元素;
$\varepsilon$;
$\emptyset$;
$(R_1\cup R_2)$, 其中$R_1$和$R_2$是正则表达式
$(R_1\circ R_2)$, 其中$R_1$和$R_2$是正则表达式
$(R_1^\ast)$, 其中$R_1$是正则表达式

用或($|$)连接一些串, 同时出现可选串$[]$. 例如
$$
R= (10 | 01) [00] 1
$$
表示语言
$$
L={101,011,10001,01001}
$$

它的原理也非常简单, 每个串都是一些仅有字母表中一个符号构成的语言的串联, 而或($|$)表示的就是$\cup$, 而$[x]$表示的是$x|\varepsilon$. 用这种方式表达的正则表达式, 就是我们常用于查询的正则表达式.

而如果或($|$)连接的是一些长度为1的串, 我们也更习惯将它表示为这些串的符号的集合, 例如$(a|b|c)^\ast$可以表示为$\{a,b,c\}^\ast$, 如果这个集合就是字母表$\Sigma$, 我们还可以写作$\Sigma^\ast$. 同时, 如果我们希望重复一个串$x$大于等于$1$次也可以用$x^+$来表示, 即$x^+=x \circ (x^\ast)$.

例子 设$\Sigma=\{0,1\}$

$0^\ast 10^\ast=\{w|w恰好有一个1\}$
$(\Sigma\Sigma\Sigma)^\ast=\{w|w的长度正好是3的倍数\}$
$2333(3^\ast)=\{w|w是由2333开头且在之后是任意长度的纯3串\}$
其中3.中表示的正则表达式有助于屏蔽弹幕中那些过长的类$233$串, 例如$2333333333333333333333$.

为了避免读者对于陌生数学符号的恐惧, 我们解释一下超集. 有限集的超集非常容易理解, 一个有限集$S$的超集, 是它的所有子集的集合, 记作$\mathcal{P}(S)$. 例如$S=\{a,b,c\}$, 那么它一共有8个子集
$$
\emptyset,\{a\},\{b\},\{c\},\{ab\},\{ac\},\{bc\},\{abc\}
$$

$\delta:Q\times\Sigma_\varepsilon \to \mathcal{P}(Q)$称为转移函数

非确定自动机的转移函数的上域(codomain)(注意不是值域!)变为了状态集$Q$的超集$\mathcal{P}(Q)$. 除此之外, 非确定自动机的转移函数还能接受输入$\varepsilon$, 即在不接受任何输入的时候也可能随机发生转移. 

引理6 泵引理

假设 ${ L\subseteq \Sigma ^{*}}$是正则语言, 存在字符串 ${ w\in L}$且${ \left|w\right|\geq n}$, 则以下说法成立：

${ \left|xy\right|\leq n}$  
${ \left|y\right|\geq 1}$  
${ \forall k\geq 0:xy^{k}z\in L}$

编写一个判定正则语言的程序$P_1:x\to \{0,1\}$, 程序的输入是一个正则表达式$R$和一个串$x$. 设正则表达式$R$表示的语言为$L$. $P_1(x)=1\iff x\in L$.