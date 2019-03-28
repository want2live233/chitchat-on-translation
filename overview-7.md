# 翻译的两难

词语是语言的基本组成单位，所以进行翻译时，也应当首先确保准确认识原文的词意，然后在目的文字中选择合适的词汇进行表达。

这个道理说起来似简单，做起来却很麻烦，因为词语的意思通常不只一种，有表意（denotation）和涵义（connotation）的区别。表意是刚性的、常见的意义，而涵义是词语蕴含的相关意义。

比如英文中的horse，表意是“马”，涵义则是“强健有力”；中文里的“牛”，表意是一种动物，涵义则是“壮实”或者“勤勉”。所以如果看到英文说“这人强壮如 **马**”，译者必须知道这里取的是涵义而不是表面的意思，所以译成中文必须改为“这人强壮如 **牛**”。

不幸的是，许多译者并不了解这方面的区别，或者即便了解也不够重视，结果难免生出问题来。我曾经翻译过一篇关于Java的 *Serialization* 的文章，刚开始翻译时并没有想太多，按照通行译法，人人都知道serialize当然就是“序列化”。不料，翻译过程中却遇到一个词非常难翻译：flatten。原文是这样的：

> 靠对象的序列化（serialization），你就能把对象flatten，用各种神奇的方式重用。

一直以来我都觉得“序列化”是术语，指把对象转换成二进制数据的过程。但是，*flatten* 的意思分明是“打扁”嘛，难道把对象“打扁”到磁盘上？看下面的句子才真正弄明白：

> the object can be flattened into bytes and subsequently inflated in the future

看来这里的flatten表达的不是“打扁”的动作，而是“打扁”的涵义：不管之前的对象有多庞大多复杂，它总可以“拆散”成一个个字节排列成的简单字节流。未来，又可以“组装”起来。如果我们把对象比作大房子，不论它多高多漂亮，最后总是能“拆”成一块块的砖，整齐地码好，之后又可以用这些砖重新建出房子来。

如果flatten从这个角度理解没错，serialize不翻译为“串行化”，而翻译成“序列化”也就顺理成章了：serial作为形容词的意义之一是：in regular succession without gaps，即“没有间隔的规律排列”，恰恰是上面说的“一个个的字节排列成的简单字节流”的意思。

所以，serialize作为表示这种意思的术语，不是石头里蹦出来，也不是拉郎配拉出来的。它原本的意思是把东西“打扁”，自然可以表示把对象拆散成普通二进制字节流。从这个意义上说，翻译成“序列化”是没错的。

那么，“串行化”的翻译也算情有可原。“串行化”的背后，我们隐约看到“前后相继的均等序列”的意思（比如“串行执行”之类），这与上面说的“序列化”是沾边的。

然而中文语境里， “**串行化**” 一般是与 “**并行化**” 对应的，用来描述指令的执行方式，读者如果要理解“拆散为二进制字节流”的“串行化”，就得脱离常见使用场景多费一番脑筋。所以尽管“串行化”与原意沾边，严谨的译者也不应该采纳。

这个小问题恰恰折射出翻译中的大困境：某种语言中的一个词，它所对应的一系列意思在这种语言关系非常紧密；如果换了语言，因为大背景不同，原来那些关系之间的关系就完全谈不上“紧密”了，甚至可能相差万里。

watch可以翻译成“手表”和“看”。在中文里这两个意思看似毫无联系，但英文里不是如此。“**手表** (*small timepiece*) ”的意思是从1588年第一次出现的，根源是1440年的“用来唤醒睡觉的人的计时装置”。watch本身就有“ *看着、提醒* (*to keep someone or something under close observation*)”的意思，所以watch可以是“手表”也可以是“看”。如果原文作者特意用双关语，用watch同时指涉“手表”和“看”，翻译起来就要多动不少脑筋。

史蒂芬·霍金写过一本科普读物，**The Universe in a Nutshell**。in a nutshell是一个短语，表示“简而言之”，“几句话就能说明白”，从这个意义上说，它可以翻译成“浅谈”之类（跟“时间简史”一致）。

但nutshell本身确实有“果壳”的意思，而且汉姆雷特说过

>哪怕身在果壳之中，我仍是无限宇宙之王

所以霍金选择Nutshell做书名是有多种意蕴的。可惜在中文里“果壳”并不能联系到这么多意思，因此无论翻译成 “**果壳中的宇宙**” 还是 “**浅谈宇宙**”，都不算错，相比原文都差了点意思。

科技翻译中这个问题更常见，尤其是IT行业的术语。因为国外的很多IT行业从业者想象力都很丰富，所以依据生活创造了大量形象的术语，这些术语在英文里都是非常容易理解的，翻译为中文之后则不是如此。

比如buffer，原来指的是 **用来减轻震荡的气垫等设备**，引申出IT行业的“缓冲”就非常自然，但在中文语境里，原始的buffer并不叫“缓冲”，而是叫“救生气垫”或“减震气垫”。“缓冲”这个名字属于针对IT这个狭窄领域重新创造的名次，强调的是“解决速度变化”的意义，与中文语境里的“救生”和“减震”并没有太多联系，所以初次接触的人往往专门学习才能明白“缓冲”的定义，甚至必须死记硬背。

Cache的情况也是这样，cache的本意是 **隐匿的存放位置**，引申出“为提高读取速度而专门提供的高速存储器”也属自然，因为懂IT的人都知道，cache通常是“透明”的，用户觉察不到。cache翻译为“缓存”，是为cache这种设备专门“量身定制”的名称，与“隐匿的存放位置”的意思完全切断了。许多人需要专门学习才知道“缓存”有什么作用，专门提醒才可以认识到cache是“透明”的。

更有意思的是boot翻译为“启动”，其实boot的意思来自bootstrap，意思是“鞋带”。因为工程师们认为计算机的启动非常矛盾，计算机必须依靠程序才能启动，而计算机不启动又没法执行程序，就好像“拽自己的鞋带把自己拉起来”的谚语一样。如果仅仅盯着“启动”，计算机启动时那种自相矛盾的局面就无从说起了。

当然，也不是所有这类问题都有遗憾，有时候“画蛇添足”想出来的翻译，会被大家接受下来，成为约定俗成的名称。最典型的例子就是two-edged sword翻译为“双刃剑”了。

如果“果壳中的宇宙”说明“双关语翻译时难以两全”，那么“双刃剑”的翻译绝对是“想当然”的后果。英文的sword的解释是

> *a weapon (as a cutlass or rapier) with a long blade for cutting or thrusting that is often used as a symbol of honor or authority*

这是一类兵器的统称，它们的刃很长，是用来切或者刺的，通常也用来作为荣誉或权威的象征。

如果仔细观察就会发现，sword的定义并没有区分刀刃的数目，所以才有*one-edged* sword, *two-edged* sword的说法。可是翻译成中文就“忠实”地变成了“双刃剑”。

可是到了中文里情况就变了，中文的“剑”一定是双刃的，那么 *single-edge sword* 是什么？其实就是“刀”嘛。所以“双刃剑”乃是“想当然”的翻译，其实属于画蛇添足，不过天长日久，已经被大家接受。但这终究是特例，不可推而广之。

试问，有谁见过“东洋单刃剑”吗？