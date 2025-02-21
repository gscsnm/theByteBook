# 5.3 Paxos 的起源

Paxos 是由 Leslie Lamport 于 1990 提出的一种基于消息传递且具有高度容错特性的协商共识算法，是当今分布式系统最重要的理论基础，几乎就是“共识”两个字的代名词。

Paxos 最初的论文名称为 《The Part-Time Parliament》，翻译成中文就是“兼职会议”，如果不事先说明，也许你根本不会认识到这一篇关于分布式的论文。Lamport 写这篇论文时，采用了一个虚构的古希腊岛屿（岛屿名称 Paxos，这也是 Paxos 算法名称的来源）上发生的故事来描述这个算法。为了说明这个算法，Lamport 做了几次演讲，在演进中 Lamport 扮演了《夺宝奇兵》中印第安纳·琼斯风格的考古学家，为了逼真 Lamport 还带上了与电影角色同款的牛仔毡帽。不幸的是 Paxos 论文中采用希腊民主议会的比喻很明显失败了，Lamport 像写小说一样，把一个复杂的数学问题弄成了一篇带有考古色彩的历史小说。听众没有记住 Paxos 算法，仅仅记住了印第安纳·琼斯。

1990 年，Lamport 将这篇论文提交给 TOCS。根据 Lamport 自己的描述[^2]，TOCS 的三个审稿人看过 Lamport 的论文后认为“该论文虽然不怎么重要但还有些意思，只是应该把其中所有 Paxos 相关的故事背景删掉”。Lamport 对这些缺乏幽默感的人颇为不爽，他不打算对论文做任何修改，从而论文的发表被搁置。

虽然论文没有发表，但并不代表没有人关注这个算法。Bulter W.Lampson（该大佬是 1991年 图灵奖获得者）认识到这个算法的重要性

多年后，两个在 SRC(Systems Research Center，DEC 于 1984 年创立，Lamport 也曾在此工作过)工作的人需要为他们正在构建的分布式系统寻找一些合适算法，而 Paxos 恰恰提供了他们想要的。Lamport 就将论文发给他们，他们也没觉得该论文有什么问题。因此，Lamport 觉得论文重新发表的时间到了，《The Part-Time Parliament》[^3] 最终在 1998 年公开发表。

可还是有很多人抱怨这篇论文看不懂，人们只记住了那个奇怪的故事，而不是 Paxos 算法。Lamport 走到哪都要被人抱怨一通。于是他忍无可忍，2001 年使用计算机领域的概念重新描述了一遍算法，并发了论文 《Paxos Made Simple》[^4]。

<div  align="center">
	<img src="../assets/paxos.png" width = "350"  align=center />
</div>

是的，你没看错，摘要只有一句话 “The Paxos algorithm, when presented in plain English, is very simple.”！

然而，这篇论文还是非常难以理解，我们引用另一篇文章中关 于Paxos 算法的描述，摘自 USENIX ATC 2013 的 Best paper《In Search of an Understandable Consensus Algorithm》，大致含义说：Paxos真的太难懂了，很少有人不付出极大努力就能完全理解。在另一个高水平会议 NSDI 上，不少人对 Paxos 感到不爽。连点评者自己都和它做了很久的斗争，所以他这篇文章取名为“寻找一种易懂的一致性算法”...意思是还在寻找中，根本不像 Lamport 说的那么简单。后人无不感到 Lamport 深深的恶意。


直到 Google 的 Chubby 横空出世，使用 Paxos 解决了分布式共识的问题，并将其整理成正式的论文发表之后，得益于 Google 的行业影响力，辅以 Chubby 作者 Mike Burrows 那略显夸张但足够吸引眼球的评价推波助澜，Paxos 逐渐被大家熟知和认可。Lamport 凭借他在分布式领域的贡献，最终于 2013 年获得图灵奖。

[^2]: 参见 https://lamport.azurewebsites.net/pubs/pubs.html#lamport-paxos
[^3]: 参见 https://lamport.azurewebsites.net/pubs/lamport-paxos.pdf
[^4]: 参见 https://lamport.azurewebsites.net/pubs/paxos-simple.pdf