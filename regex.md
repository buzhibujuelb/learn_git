# 正则表达式

<style type="text/css">table  {border-collapse:collapse;border-spacing:0;}table td{border-color:black;border-style:solid;border-width:1px;font-family:Arial, sans-serif;font-size:14px;  overflow:hidden;padding:10px 5px;word-break:normal;}table th{border-color:black;border-style:solid;border-width:1px;font-family:Arial, sans-serif;font-size:14px;  font-weight:normal;overflow:hidden;padding:10px 5px;word-break:normal;}table{border-color:inherit;text-align:left;vertical-align:top}</style>

<table cellspacing="0"><caption>表1.常用的元字符</caption><thead><tr><th scope="col">代码</th><th scope="col">说明</th></tr></thead><tbody><tr><td><span class="code">.</span></td><td><span class="desc">匹配除换行符以外的任意字符</span></td></tr><tr><td><span class="code">\w</span></td><td><span class="desc">匹配字母或数字或下划线或汉字</span></td></tr><tr><td><span class="code">\s</span></td><td><span class="desc">匹配任意的空白符</span></td></tr><tr><td><span class="code">\d</span></td><td><span class="desc">匹配数字</span></td></tr><tr><td><span class="code">\b</span></td><td><span class="desc">匹配单词的开始或结束</span></td></tr><tr><td><span class="code">^</span></td><td><span class="desc">匹配字符串的开始</span></td></tr><tr><td><span class="code">$</span></td><td><span class="desc">匹配字符串的结束</span></td></tr></tbody></table>
<table cellspacing="0"><caption>表2.常用的限定符</caption><thead><tr><th scope="col">代码/语法</th><th scope="col">说明</th></tr></thead><tbody><tr><td><span class="code">*</span></td><td><span class="desc">重复零次或更多次</span></td></tr><tr><td><span class="code">+</span></td><td><span class="desc">重复一次或更多次</span></td></tr><tr><td><span class="code">?</span></td><td><span class="desc">重复零次或一次</span></td></tr><tr><td><span class="code">{n}</span></td><td><span class="desc">重复n次</span></td></tr><tr><td><span class="code">{n,}</span></td><td><span class="desc">重复n次或更多次</span></td></tr><tr><td><span class="code">{n,m}</span></td><td><span class="desc">重复n到m次</span></td></tr></tbody></table>
<table cellspacing="0"><caption>表3.常用的反义代码</caption><thead><tr><th scope="col">代码/语法</th><th scope="col">说明</th></tr></thead><tbody><tr><td><span class="code">\W</span></td><td><span class="desc">匹配任意不是字母，数字，下划线，汉字的字符</span></td></tr><tr><td><span class="code">\S</span></td><td><span class="desc">匹配任意不是空白符的字符</span></td></tr><tr><td><span class="code">\D</span></td><td><span class="desc">匹配任意非数字的字符</span></td></tr><tr><td><span class="code">\B</span></td><td><span class="desc">匹配不是单词开头或结束的位置</span></td></tr><tr><td><span class="code">[^x]</span></td><td><span class="desc">匹配除了x以外的任意字符</span></td></tr><tr><td><span class="code">[^aeiou]</span></td><td><span class="desc">匹配除了aeiou这几个字母以外的任意字符</span></td></tr></tbody></table>
<table cellspacing="0"><caption>表4.常用分组语法</caption><tbody><tr><th scope="col">分类</th><th scope="col">代码/语法</th><th scope="col">说明</th></tr><tr><th rowspan="3">捕获</th><td><span class="code">(exp)</span></td><td><span class="desc">匹配exp,并捕获文本到自动命名的组里</span></td></tr><tr><td><span class="code">(?&lt;name&gt;exp)</span></td><td><span class="desc">匹配exp,并捕获文本到名称为name的组里，也可以写成(?'name'exp)</span></td></tr><tr><td><span class="code">(?:exp)</span></td><td><span class="desc">匹配exp,不捕获匹配的文本，也不给此分组分配组号</span></td></tr><tr><th rowspan="4">零宽断言</th><td><span class="code">(?=exp)</span></td><td><span class="desc">匹配exp前面的位置</span></td></tr><tr><td><span class="code">(?&lt;=exp)</span></td><td><span class="desc">匹配exp后面的位置</span></td></tr><tr><td><span class="code">(?!exp)</span></td><td><span class="desc">匹配后面跟的不是exp的位置</span></td></tr><tr><td><span class="code">(?&lt;!exp)</span></td><td><span class="desc">匹配前面不是exp的位置</span></td></tr><tr><th rowspan="1">注释</th><td><span class="code">(?#comment)</span></td><td><span class="desc">这种类型的分组不对正则表达式的处理产生任何影响，用于提供注释让人阅读</span></td></tr></tbody></table>
<table cellspacing="0"><caption>表5.懒惰限定符</caption><thead><tr><th scope="col">代码/语法</th><th scope="col">说明</th></tr></thead><tbody><tr><td><span class="code">*?</span></td><td><span class="desc">重复任意次，但尽可能少重复</span></td></tr><tr><td><span class="code">+?</span></td><td><span class="desc">重复1次或更多次，但尽可能少重复</span></td></tr><tr><td><span class="code">??</span></td><td><span class="desc">重复0次或1次，但尽可能少重复</span></td></tr><tr><td><span class="code">{n,m}?</span></td><td><span class="desc">重复n到m次，但尽可能少重复</span></td></tr><tr><td><span class="code">{n,}?</span></td><td><span class="desc">重复n次以上，但尽可能少重复</span></td></tr></tbody></table>
<table cellspacing="0"><caption>表6.常用的处理选项</caption><thead><tr><th scope="col">名称</th><th scope="col">说明</th></tr></thead><tbody><tr><td>IgnoreCase(忽略大小写)</td><td>匹配时不区分大小写。</td></tr><tr><td>Multiline(多行模式)</td><td>更改<span class="code">^</span>和<span class="code">$</span>的含义，使它们分别在任意一行的行首和行尾匹配，而不仅仅在整个字符串的开头和结尾匹配。(在此模式下,<span class="code">$</span>的精确含意是:匹配\n之前的位置以及字符串结束前的位置.)</td></tr><tr><td>Singleline(单行模式)</td><td>更改<span class="code">.</span>的含义，使它与每一个字符匹配（包括换行符\n）。</td></tr><tr><td>IgnorePatternWhitespace(忽略空白)</td><td>忽略表达式中的非转义空白并启用由<span class="code">#</span>标记的注释。</td></tr><tr><td>ExplicitCapture(显式捕获)</td><td>仅捕获已被显式命名的组。</td></tr></tbody></table>
<table cellspacing="0"><caption>表7.尚未详细讨论的语法</caption><thead><tr><th scope="col">代码/语法</th><th scope="col">说明</th></tr></thead><tbody><tr><td><span class="code">\a</span></td><td><span class="desc">报警字符(打印它的效果是电脑嘀一声)</span></td></tr><tr><td><span class="code">\b</span></td><td><span class="desc">通常是单词分界位置，但如果在字符类里使用代表退格</span></td></tr><tr><td><span class="code">\t</span></td><td><span class="desc">制表符，Tab</span></td></tr><tr><td><span class="code">\r</span></td><td><span class="desc">回车</span></td></tr><tr><td><span class="code">\v</span></td><td><span class="desc">竖向制表符</span></td></tr><tr><td><span class="code">\f</span></td><td><span class="desc">换页符</span></td></tr><tr><td><span class="code">\n</span></td><td><span class="desc">换行符</span></td></tr><tr><td><span class="code">\e</span></td><td><span class="desc">Escape</span></td></tr><tr><td><span class="code">\0nn</span></td><td><span class="desc">ASCII代码中八进制代码为nn的字符</span></td></tr><tr><td><span class="code">\xnn</span></td><td><span class="desc">ASCII代码中十六进制代码为nn的字符</span></td></tr><tr><td><span class="code">\unnnn</span></td><td><span class="desc">Unicode代码中十六进制代码为nnnn的字符</span></td></tr><tr><td><span class="code">\cN</span></td><td><span class="desc">ASCII控制字符。比如\cC代表Ctrl+C</span></td></tr><tr><td><span class="code">\A</span></td><td><span class="desc">字符串开头(类似^，但不受处理多行选项的影响)</span></td></tr><tr><td><span class="code">\Z</span></td><td><span class="desc">字符串结尾或行尾(不受处理多行选项的影响)</span></td></tr><tr><td><span class="code">\z</span></td><td><span class="desc">字符串结尾(类似$，但不受处理多行选项的影响)</span></td></tr><tr><td><span class="code">\G</span></td><td><span class="desc">当前搜索的开头</span></td></tr><tr><td><span class="code">\p{name}</span></td><td><span class="desc">Unicode中命名为name的字符类，例如\p{IsGreek}</span></td></tr><tr><td><span class="code">(?&gt;exp)</span></td><td><span class="desc">贪婪子表达式</span></td></tr><tr><td><span class="code">(?&lt;x&gt;-&lt;y&gt;exp)</span></td><td><span class="desc">平衡组</span></td></tr><tr><td><span class="code">(?im-nsx:exp)</span></td><td><span class="desc">在子表达式exp中改变处理选项</span></td></tr><tr><td><span class="code">(?im-nsx)</span></td><td><span class="desc">为表达式后面的部分改变处理选项</span></td></tr><tr><td><span class="code">(?(exp)yes|no)</span></td><td><span class="desc">把exp当作零宽正向先行断言，如果在这个位置能匹配，使用yes作为此组的表达式；否则使用no</span></td></tr><tr><td><span class="code">(?(exp)yes)</span></td><td><span class="desc">同上，只是使用空表达式作为no</span></td></tr><tr><td><span class="code">(?(name)yes|no)</span></td><td><span class="desc">如果命名为name的组捕获到了内容，使用yes作为表达式；否则使用no</span></td></tr><tr><td><span class="code">(?(name)yes)</span></td><td><span class="desc">同上，只是使用空表达式作为no</span></td></tr></tbody></table>

方括号缺省具有特殊含义，因此不用转义。
圆括号会按原义匹配字符(及)，因此需要转义，使其具有特殊含义。花括号也一样需要转义，不过，只需为开括号转义，而与之对应的闭括号
则不用，因为Vim会推测我们的意图。圆括号的情况有所不同，无论开闭括号都必须转义。

\m magic
\M nomagic

\v very magic
\V very nomagic

\c 忽略大小写
\C 强制大小写

smartcase 覆盖 ignorecase

元字符 \zs标志着一个匹配的起始，元字符 \ze则用来界定匹配的结束。


\0 插入匹配模式的所有内容

& 插入匹配模式的所有内容

\={Vim script} 执行 {Vim Script} 表达式；并将返回的结果作为替换 {string}

在Vim中，通过调用函数 submatch(0)，即可得到当前匹配的内容

:%s//\=submatch(0)-1/g

单词边界 < > （需转义）

