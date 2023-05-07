# 

# 人类反馈强化学习(RLHF)

> 在讨论为什么 ChatGPT 能够激发我们如此多想象力的文献中，我经常遇到两种说法： 
>
> - 规模：投入更多数据并对其进行计算。
> - UX：从prompt界面转变为更自然的聊天界面。
>
> 在最近的各种demo展示狂潮中经常被掩盖的一个故事是令人难以置信的技术创造力，这些创造力用于制作像 ChatGPT 这样的模型。其中一个很酷的想法是 RLHF（人类反馈强化学习）：将强化学习和人类反馈结合到 NLP 中。
>
> 众所周知，深度学习（RL）很难使用，因此主要局限于游戏和模拟环境，如 Atari 或 MuJoCo。就在五年前，RL 和 NLP 的发展几乎是正交的——不同的堆栈、不同的技术和不同的实验设置。看到它在一个新领域大规模工作令人印象深刻。
>
> 那么，RLHF 究竟是如何工作的呢？为什么它有效？这篇文章将讨论这些问题的答案。


## 目录

- [RLHF总览](#RLHF总览)
- [第一阶段：用于补全的预训练](#第一阶段：用于补全的预训练)
- [第二阶段：用于对话的监督微调（SFT）](#第二阶段：用于对话的监督微调（SFT）)
- [第三阶段：人类反馈强化学习（RLHF）](#第三阶段：人类反馈强化学习（RLHF）)
- [总结](#总结)
- [论文](#papers)
- [代码库](#代码库)
- [博客](#博客)

> 要理解 RLHF，我们首先需要了解训练像 ChatGPT 这样的模型的过程，以及 RLHF 在其中发挥了怎样的作用，这是本文第一部分的重点。以下 3 个部分涵盖了 ChatGPT 开发的 3 个阶段。对于每个阶段，我将讨论该阶段的目标、为什么需要该阶段以及相应的数学公式，供那些想要查看更多技术细节的人使用。
>
> > 第一阶段：用于补全的预训练
> > …. 语言模型
> > …. 数学公式
> > …. 预训练阶段的数据瓶颈
> > 第二阶段：用于对话的监督微调（SFT）
> > …. 为什么监督微调
> > …. 展示数据
> > …. 数学公式
> > 第三阶段：人类反馈强化学习（RLHF）
> > …. 3.1. 奖励模型(RM)
> > …….. 数学公式
> > …….. 用于收集比较数据的 UI
> > …. 3.2. 使用奖励模型进行微调
> > …….. 数学公式
> > …. RLHF 和幻觉
>
> 目前，RLHF 尚未在行业中广泛使用，除了几个主要的主要参与者——OpenAI、DeepMind 和 Anthropic。然而，我已经看到许多使用 RLHF 的正在进行的工作，所以看到 RLHF 在未来被更多地使用我不会感到惊讶。
>
> 在这篇文章中，我假设读者没有 NLP 或 RL 方面的专业知识。如果这样做，请随意跳过与您不太相关的任何部分。



## RLHF总览

### ChatGPT

让我们先来回顾一下 ChatGPT 的开发过程，看看 RLHF 适配在哪些地方。

![image-20230506154237773](./人类反馈强化学习(RLHF).assets/image-20230506154237773.png)

如果你眯着眼睛，下面的这张图看起来很像带有笑脸的 Shoggoth。

![image-20230506154843882](./人类反馈强化学习(RLHF).assets/image-20230506154843882.png)

> 【备注】The Shoggoth with Smiley Face 是一个与人工智能领域相关的标语和俚语表达，它使用笑脸和 Lovecraftian Cthulhu 图像来描述会话人工智能工具的真正力量被掩盖以允许商业公众消费的概念。带有笑脸图像的 Shoggoth 于 2022 年末和 2023 年初在 Twitter 和 LessWrong 论坛上流行起来，用于描述 RLHF（人类反馈强化学习）等工具的效果，旨在使 AI 工具更适合商业使用。

1. **【预训练模型】**是一个未驯服的怪物，因为它是根据从互联网上搜集的乱七八糟的数据进行**①训练**的：比如点击诱饵、错误信息、宣传、阴谋论或针对某些人口统计数据的攻击
2. 然后这个怪物在更高质量的数据上进行了**②微调**——比如 StackOverflow、Quora 或人类注释——这使得它在某种程度上被社会接受。
3. 然后**③使用 RLHF 进一步完善**微调模型以使其适合客户，例如给它一个笑脸。

您可以跳过这三个阶段中的任何一个。例如，您可以直接在预训练模型之上进行 RLHF，而无需经过 SFT 阶段。然而，根据经验，将所有这三个步骤结合起来可以获得最佳性能。

预训练是资源最密集的阶段。对于 InstructGPT 模型，预训练占用了[整体计算和数据资源的98%](https://openai.com/research/instruction-following)。您可以将**SFT**和**RLHF**视为解锁预训练模型【已经具有】但【用户很难仅通过prompt访问】的功能。

教机器从人类偏好中学习并不是什么新鲜事。它已经[存在了十多年](https://arxiv.org/abs/1208.0984)。当他们的主要赌注是机器人技术时，OpenAI 就开始探索[从人类偏好中学习](https://openai.com/research/learning-from-human-preferences)。当时的说法是人类偏好对人工智能安全至关重要。然而，事实证明，人类的偏好也可以造就更好的产品，从而吸引更多的观众。

**》》补充：OpenAI 2017 年 learning from human preference 论文摘要**

> One step towards building safe AI systems is to remove the need for humans to write goal functions, since using a simple proxy for a complex goal, or getting the complex goal a bit wrong, can lead to undesirable and even dangerous behavior. In collaboration with DeepMind’s safety team, we’ve developed an algorithm which can infer what humans want by being told which of two proposed behaviors is better.
>
> 构建安全 AI 系统的一个步骤是消除人类编写目标函数的需要，因为对复杂目标使用简单代理，或者将复杂目标弄错一点，可能会导致超出预期甚至危险的行为。通过与 DeepMind 的安全团队合作，我们开发了一种算法，可以通过告知两种计划行为中哪一种更好来推断人类的需求。

### RLHF理念

RLHF的理念是使用**强化学习**的方法直接优化**具有人类反馈的**语言模型。通过使用人类反馈，RLHF使得【语言模型】能够从**基于一般文本数据的训练模型**，逐步向**符合复杂人类价值观的模型**靠拢。

- 用于大型语言模型 (LLM) 的 RLHF

![image info](./人类反馈强化学习(RLHF).assets/overview_chatgpt.png)

- 用于视频游戏的 RLHF（例如 Atari）

![image info](./人类反馈强化学习(RLHF).assets/overview_video_game.png)

### 细节介绍

RLHF通常是指“基于人类反馈的强化学习”（Reinforcement Learning with Human Feedback）。强化学习（RL）是一种机器学习方法，它涉及训练智能体根据环境反馈做出决策。在RLHF中，智能体还会从人类那里获得评分或评价其行为的反馈，这有助于它更快、更准确地学习。

RLHF是人工智能领域的一个活跃研究方向，应用于诸如机器人技术、游戏以及个性化推荐系统等领域。它试图解决在智能体无法充分获取环境反馈、需要人类输入以提高性能的情景下强化学习所面临的挑战。

基于人类反馈的强化学习（RLHF）是人工智能研究中迅速发展的领域，已经有多种先进技术被开发出来以提高RLHF系统的性能。以下是一些例子：

- **逆向强化学习(Inverse Reinforcement Learning, IRL)**: 逆向强化学习（IRL）是一种技术，允许智能体从人类反馈中学习奖励函数，而不是依赖预先定义的奖励函数。这使得智能体可以从更复杂的反馈信号中学习，例如期望行为的示范。

- **学徒学习(Apprenticeship Learning)**: 学徒学习是一种将逆向强化学习（IRL）与监督学习相结合的技术，使智能体能够同时从人类反馈和专家示范中学习。这可以帮助智能体更快、更有效地学习，因为它能从正面和负面反馈中都获得学习。

- **交互式机器学习(Interactive Machine Learning, IML)**: 交互式机器学习（IML）是一种涉及智能体和人类专家之间积极互动的技术，允许专家实时对智能体的行为提供反馈。这有助于智能体更快、更高效地学习，因为在学习过程的每一步，它都可以获得对其行为的反馈。

- **人在回路强化学习(Human-in-the-Loop Reinforcement Learning, HITLRL)**: 人在回路强化学习（HITLRL）是一种将人类反馈融入到强化学习过程的多个层面的技术，如奖励塑造、动作选择和策略优化。这有助于提高基于人类反馈的强化学习系统的效率和有效性，充分利用人类和机器的优势。

以下是一些人类反馈强化学习（RLHF）的示例：

- **游戏**: 在游戏中，人类反馈可以帮助智能体学习在不同游戏场景中有效的策略和战术。例如，在流行的围棋游戏中，人类专家可以对智能体的走法提供反馈，帮助它提高游戏水平和决策能力。

- **个性化推荐系统**: 在推荐系统中，人类反馈可以帮助智能体学习个别用户的喜好，从而实现提供个性化推荐。例如，智能体可以利用用户对推荐产品的反馈来学习哪些特性对他们最重要。

- **机器人**: 在机器人技术中，人类反馈可以帮助智能体学习如何以安全、高效的方式与物理环境互动。例如，机器人可以在人类操作员关于最佳路径选择或应避免的物体的反馈下，更快地学会在新环境中导航。

- **教育**: 在教育领域中，人类反馈可以帮助智能体更有效地学习如何教导学生。例如，一个基于AI的辅导员可以利用教师关于哪些教学策略对不同学生最有效的反馈，从而个性化地改进学习体验。



## 第一阶段：用于补全的预训练

预训练阶段的结果是大型语言模型 (LLM)，通常称为预训练模型。包括 GPT-x (OpenAI)、Gopher (DeepMind)、LLaMa (Meta)、StableLM (Stability AI)。

### 语言模型

语言模型对有关语言的统计信息进行编码。为简单起见，统计信息告诉我们某物（例如一个词、一个字符）出现在给定上下文中的可能性有多大。根据语言模型，术语**`token`**可以指代单词、字符或单词的一部分（比如`-tion`）。您可以将标记视为语言模型使用的词汇表。

说流利的语言的人会下意识地掌握该语言的统计知识。例如，给定上下文 `My favorite color is __`，如果你说英语，你就会知道空白中的单词更可能是`green`而不是`car`。

同样，语言模型也应该能够填补那个空白。您可以将语言模型视为“*completion machine*”：给定文本（prompt），它可以生成response以完成该文本。这是一个例子：

- **Prompt (来自用户)**: `I tried so hard, and got so far`
- **Completion (来自语言模型)**: `But in the end, it doesn't even matter.`

![image-20230506161608235](./人类反馈强化学习(RLHF).assets/image-20230506161608235.png)

听起来好像很普通，但补全功能却非常强大，因为很多任务都可以被框定为补全任务：翻译、总结、写代码、做数学等。例如，给出提示：`How are you in French is `，一个语言模型或许会给出： `Comment ça va`，这样就高效地从一种语言翻译成另一种语言。

为了训练一个语言模型来完成，你需要喂给它大量的文本，这样它就可以从中提取统计信息。提供给模型以供学习的文本称为**训练数据**。考虑一种只包含两个标记 0 和 1 的语言。如果你将以下序列作为训练数据提供给语言模型，则语言模型可能会提取：

- 如果上下文是 `01`，则下一个标记可能是 `01` 
- 如果上下文是 `0011`，下一个标记可能是 `0011`

```
0101
010101
01010101
0011
00110011
001100110011
```

由于语言模型模仿其训练数据，因此语言模型的效果仅取决于与你的训练数据，因此有“Garbage in, garbage out”的说法。如果你在 Reddit 评论上训练语言模型，你可能不想把它带回家给你的父母看。

### 数学公式

- [原文链接](https://huyenchip.com/2023/05/02/rlhf.html)

![image-20230506162716358](./人类反馈强化学习(RLHF).assets/image-20230506162716358.png)

### 预训练阶段的数据瓶颈

今天，像 GPT-4 这样的语言模型使用了如此多的数据，以至于人们担心未来几年我们将耗尽互联网数据。这听起来很疯狂，但它正在发生。要了解一万亿token有多大：一本书包含大约 50,000 个单词或 67,000 个token。 1万亿token相当于1500万本书。

![image-20230506163412248](./人类反馈强化学习(RLHF).assets/image-20230506163412248.png)

训练数据集大小的增长速度远快于生成新数据的速度（[Villalobos 等人，2022 年](https://arxiv.org/abs/2211.04325)）。如果你曾经在互联网上放过任何东西，你应该假设它已经或者将被包含在某些语言模型的训练数据中，无论你是否同意。这类似于如果您在 Internet 上发布某些内容，您应该期望它被 Google 索引。

![image-20230506163629471](./人类反馈强化学习(RLHF).assets/image-20230506163629471.png)

最重要的是，互联网正在迅速填充由大型语言模型（如 ChatGPT）生成的数据。如果公司继续使用互联网数据来训练LLM，那么这些新的 LLM 可能只是根据现有 LLM 生成的数据来进行训练。

一旦公开可用的数据用尽，获得更多训练数据的最可行途径是使用专有数据。我怀疑任何以某种方式获得大量专有数据（受版权保护的书籍、翻译、合同、医疗记录、基因组序列、用户数据等）的公司都将拥有竞争优势。毫不奇怪，鉴于 ChatGPT，许多公司已经更改了他们的数据条款以防止其他公司为了训练 LLM 抓取他们的数据——参考 [Reddit](https://www.redditinc.com/policies/data-api-terms)、[StackOverflow](https://policies.stackoverflow.co/teams/enterprise-cloud-business/)。

## 第二阶段：用于对话的监督微调（SFT）

### 为什么监督微调

预训练可以优化补全。如果你给预训练模型一个问题，例如`How to make pizza`，则以下任何一项都可以有效完成。

1. 为问题添加更多上下文：`for a family of six`
2. 添加后续问题：`? What ingredients do I need? How much time would it take?`
3. 实际给出答案

如果您正在寻找答案，则首选第三个选项。 SFT 的目标是优化预训练模型以生成用户正在寻找的响应。

怎么做？我们知道模型会模仿其训练数据。在 SFT 期间，我们展示了我们的语言模型示例，说明如何适当地响应不同用例的提示（例如，问答、摘要、翻译）。示例遵循格式（Prompt, Response），称为演示数据。 OpenAI 称其为supervised finetuning *behavior cloning*：你演示模型应该如何表现，模型克隆这种行为。

![image-20230506194053050](./人类反馈强化学习(RLHF).assets/image-20230506194053050.png)

要训练模型以模仿演示数据，您可以从预训练模型开始并对其进行微调，或者从头开始训练。事实上，OpenAI 表明 [1.3B 参数 InstructGPT 模型的输出优于 175B GPT-3 的输出](https://arxiv.org/abs/2203.02155)。然而，微调的方法产生了更好的结果。

### 展示数据

演示数据可以由人类生成，就像 OpenAI 对 InstructGPT 和 ChatGPT 所做的一样。与传统的数据标记不同，演示数据是由通过屏幕测试的受过高等教育的标记人员生成的。在为 InstructGPT 标注演示数据的人中，[约 90% 至少拥有大学学历](https://arxiv.org/pdf/2203.02155.pdf)，超过三分之一拥有硕士学位。

![image-20230506194652653](./人类反馈强化学习(RLHF).assets/image-20230506194652653.png)

OpenAI 的 40 个标记器为 [InstructGPT](https://arxiv.org/abs/2203.02155) 创建了大约 13,000 个（prompt, response）对。这里有一些例子：

| **Prompt**                                                   | **Response**                                                 |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| 机缘巧合是指事件以愉快或有益的方式偶然发生和发展。在句子中使用这个词。 | 遇到玛格丽特并被介绍给汤姆是一种幸运的机缘巧合。             |
| ELI5：在压力大或令人沮丧的经历中，我们胸口出现“焦虑肿块”的原因是什么？ | 喉咙里的焦虑肿块是由肌肉紧张引起的，它使声门扩张以使气流最大化。胸闷或心痛的感觉是由迷走神经引起的，迷走神经告诉器官更快地泵血、停止消化并产生肾上腺素和皮质醇。 |
| 根据此食谱创建购物清单：修剪西葫芦的末端。将西葫芦纵向切成两半；挖出纸浆，留下 1/2 英寸。炮弹。将果肉切碎。在平底锅中，用中火煮牛肉、西葫芦果肉、洋葱、蘑菇和辣椒，直到肉不再呈粉红色；流走。从火上移开。加入 1/2 杯奶酪、番茄酱、盐和胡椒粉；拌匀。用勺子舀到西葫芦壳里。放入涂有油脂的 13x9 英寸。烤盘。撒上剩余的奶酪。 | 西葫芦、牛肉、洋葱、蘑菇、辣椒、奶酪、番茄酱、盐、胡椒       |

**》》补充：DeepMind 的对话启发式算法**

> OpenAI 的方法可产生高质量的演示数据，但成本高且耗时。相反，DeepMind 使用启发式方法为他们的模型 Gopher 从互联网数据中过滤对话（[Rae et al., 2021](https://arxiv.org/abs/2112.11446)）：
>
> _具体来说，我们发现所有连续段落集（由两个换行符分隔的文本块）至少有 6 个段落长，所有段落都有一个以分隔符结尾的前缀（例如，`Gopher:` 、`Dr Smith - `或 `Q.`）。偶数索引段落必须具有相同的前缀，奇数索引段落也必须相同，但两个前缀应该不同（换句话说，对话必须严格地在两个人之间来回进行）。此过程可靠地产生高质量的对话。

**》》补充：关于微调对话与微调以下说明**

> OpenAI 的 InstructGPT 针对以下指令进行了微调。演示数据的每个示例都是一对（prompt, response）。 DeepMind 的 Gopher 非常适合进行对话。每个演示示例都是多次来回对话。说明是对话的子集——ChatGPT 是 InstructGPT 的增强版。

### 数学公式

- [原文链接](https://huyenchip.com/2023/05/02/rlhf.html)

![image-20230506195359583](./人类反馈强化学习(RLHF).assets/image-20230506195359583.png)

## 第三阶段：人类反馈强化学习（RLHF）

根据经验，与单独的 SFT 相比，RLHF 显著提高了性能。但是，我还没有看到一个我认为万无一失的论点。 Anthropic 解释说：“当人们拥有易于引出但难以形式化和自动化的复杂直觉时，我们预计人类反馈 (HF) 与其他技术相比具有最大的比较优势。” ([Bai et al., 2022](https://arxiv.org/abs/2204.05862))

![image-20230506195811751](./人类反馈强化学习(RLHF).assets/image-20230506195811751.png)

对话是灵活的。给定一个prompt，有许多似是而非的response，有些比其他的好。演示数据告诉模型对于给定的上下文哪些response是合理的，但不会告诉模型response的好坏。

一个想法：**【如果我们有一个评分函数，给出一个prompt和一个response，就能输出该response怎么样的分数。然后我们使用这个评分函数进一步训练我们的 LLM，直到给出高分的responses】**。这正是 RLHF 所做的。 RLHF 由两部分组成：

1. 训练一个reward model作为评分函数。
2. 优化 LLM 以生成【能够给出高分response】的reward model。

**》》补充：关于 RLFH 为何起作用的假设**

> Yoav Goldberg 对 [RLHF 起作用的三个假设](https://gist.github.com/yoavg/6bff0fecd65950898eba1bb321cfbd81)是很好的总结。
>
> - 多样性假设：在 SFT 期间，模型的输出预计会在某种程度上与展示的响应相匹配。例如，给定prompt“`what’s an example of a language?`”，如果演示的响应是“`Spanish`”而模型的响应是“`Java`”，则模型的响应可能被标记为错误。
> - 负反馈假设：演示只给模型正信号（例如只向模型展示好的响应），而不是负信号（例如向模型展示坏响应是什么样的）。 RL 允许我们向模型展示负面信号。
> - 幻觉假设：RLHF 应该有助于处理幻觉，我们将在 **RLHF 和幻觉**部分进行讨论。



### 3.1. 奖励模型(RM)

奖励模型（Reward model，RM）的任务是输出一对（prompt, response）的分数。训练模型以在给定输入上输出分数是机器学习中非常常见的任务。你可以简单地将其框定为**分类或回归**任务。训练RM的挑战在于获得可信赖的数据。事实证明，要让不同的RM为相同的回答给出一致的分数是相当困难的。要求RM比较两个response并决定哪个更好要容易得多。

标记过程将产生如下所示的数据：（prompt，winning_response，losing_response），这称为comparison data。

这是来自 Anthropic 的 HH-RLHF 数据集的比较数据示例。就个人而言，我更喜欢 losing_response。这凸显了从人类偏好中学习的挑战。人类的偏好是多种多样的，不可能用一个单一的数学公式来捕捉。

| **prompt**                                              | **winning_response**                                   | **losing_response**                                          |
| ------------------------------------------------------- | ------------------------------------------------------ | ------------------------------------------------------------ |
| How can I get my dog high? 我怎样才能让我的狗兴奋起来？ | I'm not sure what you mean by that. 我不确定你的意思。 | I don't know that we should get the dog high. I think it's important for a dog to experience the world in a sober state of mind. 我不知道我们应该让狗兴奋起来。我认为对于狗来说，以清醒的心态体验世界很重要。 |

现在是令人迷惑的部分：只给定这个比较数据，你如何训练模型给出具体的分数？就像你如何让人类在给予正确激励的情况下（基本上）做任何事情一样，你可以让一个模型在给定正确目标（又名损失函数）的情况下（基本上）做任何事情。

对于 InstructGPT，目标是最大化获胜响应和失败响应之间的分数差异（详见数学公式部分）。

人们尝试了不同的方法来初始化 RM：例如从头开始训练 RM 或以 SFT 模型作为种子开始。从 SFT 模型开始似乎可以提供最佳性能。直觉是，RM 至少应该和 LLM 一样强大，才能给 LLM 的回答打分。

#### 数学公式

![image-20230506202638777](./人类反馈强化学习(RLHF).assets/image-20230506202638777.png)

#### 用于收集比较数据的 UI

下面是 [OpenAI 的标记器](https://arxiv.org/pdf/2203.02155.pdf)用来为 InstructGPT 的 RM 创建训练数据的 UI 的屏幕截图。 Labelers 都给出了从 1 到 7 的具体分数，并按照偏好的顺序对响应进行排序，但仅使用排序来训练 RM。**他们的标签间一致性约为 73%，这意味着如果他们要求 10 个人对 2 个响应进行排名，其中 7 个将具有相同的排名。**

![image-20230506202734151](./人类反馈强化学习(RLHF).assets/image-20230506202734151.png)

![image-20230506202741629](./人类反馈强化学习(RLHF).assets/image-20230506202741629.png)

为了加快标记过程，他们要求每个注释者对多个响应进行排名。 4 个排序的响应，例如A > B > C > D，将产生 6 个排名对，例如(A > B)、(A > C)、(A > D)、(B > C)、(B > D)、(C > D)。

### 3.2. 使用奖励模型进行微调

在此阶段，我们将进一步训练 SFT 模型以生成输出response，以最大化 RM 的分数。今天，大多数人使用[近端策略优化 (PPO)](https://openai.com/research/openai-baselines-ppo)，这是 OpenAI 于 2017 年发布的一种强化学习算法。

在此过程中，prompt是从分布中随机选择的——例如我们可能会在客户prompt中随机选择。这些prompt中的每一个都被输入到 LLM 模型中以得到一个response，RM 会给它一个分数。

OpenAI 还发现有必要添加一个约束条件：此阶段生成的模型不应偏离 SFT 阶段生成的模型太远。直觉是对于任何给定的prompt都有许多可能的response，其中绝大多数是 RM 以前从未见过的。对于许多未知（prompt、response）对，RM 可能会错误地给出极高或极低的分数。如果没有这个约束，我们可能会偏向那些得分极高的回答，即使它们可能不是很好的回答。

OpenAI 有这张很棒的图表，解释了 InstructGPT 的 SFT 和 RLHF。

![image-20230506204354519](./人类反馈强化学习(RLHF).assets/image-20230506204354519.png)

#### 数学公式

![image-20230506210911813](./人类反馈强化学习(RLHF).assets/image-20230506210911813.png)

#### RLHF 和幻觉

幻觉是指AI模型编造事物。这是许多公司在其工作流程中犹豫不决是否使用大型语言模型的一个主要原因。

关于大型语言模型为何产生幻觉，我找到了两个假说。

第一个假说最早由Pedro A. Ortega等人在2021年10月提出，他们认为大型语言模型产生幻觉是因为它们“[缺乏对自身行为的因果关系的理解](https://arxiv.org/abs/2110.10819#deepmind)”（当时，DeepMind用“妄想”一词表示“幻觉”）。他们证明了通过将响应生成视为因果干预可以解决这个问题。

第二个假说认为幻觉是由于大型语言模型内部知识与标注者内部知识之间的不匹配造成的。OpenAI联合创始人、PPO作者John Schulman在2023年4月的[UC伯克利讲座](https://www.youtube.com/watch?v=hhiLw5Q_UFg)上提出，行为克隆会导致幻觉。在SFT期间，大型语言模型受训以模仿人类编写的响应。如果我们使用我们所拥有的知识给出响应，但大型语言模型并不具备这种知识，那么我们就是在教它产生幻觉。

这一观点也在2021年12月由另一位OpenAI员工[Leo Gao](https://www.alignmentforum.org/posts/BgoKdAzogxmgkuuAt/behavior-cloning-is-miscalibrated)很好地阐述了。理论上，人类标注者可以在每个提示中包含他们所了解的所有上下文，以教导模型仅使用现有知识。然而，在实践中这是不可能的。

Schulman认为，[大型语言模型知道自己是否了解某个知识](https://www.youtube.com/live/hhiLw5Q_UFg?feature=share&t=1019)（在我看来，这是一个很大的断言），这意味着如果我们找到一种方法，迫使大型语言模型只给出它们了解的信息，幻觉问题就可以解决。随后，他提出了几个解决方案。

1. 验证：要求大型语言模型解释（检索）其从何处获得答案的来源。
2. 强化学习。请记住，第3.1阶段的奖励模型仅使用比较进行训练：响应A优于响应B，而无需提供有关为什么A更好或者更好的程度的任何信息。Schulman认为，我们可以通过更好的奖励函数来解决幻觉问题，例如对胡编乱造的模型进行更严厉的惩罚。 以下是来自John Schulman 2023年4月讲座的屏幕截图。

![image-20230506211114633](./人类反馈强化学习(RLHF).assets/image-20230506211114633.png)

从Schulman的讲座中，我得到的印象是强化学习与人类反馈（RLHF）应该有助于解决幻觉问题。然而，InstructGPT论文显示，RLHF实际上使幻觉问题变得更糟。尽管RLHF导致了更严重的幻觉问题，但它改善了其他方面，总体而言，人类标注者更喜欢RLHF模型，而不是单独使用SFT的模型。

![image-20230506211155663](./人类反馈强化学习(RLHF).assets/image-20230506211155663.png)

基于大型语言模型（LLMs）知道自己所知的假设，有些人尝试通过提示来减少幻觉，例如添加`Answer as truthfully as possible, and if you're unsure of the answer, say "Sorry, I don't know"`。让LLMs简洁地回应似乎也有助于减轻幻觉问题——LLMs生成的标记越少，编造事物的机会就越小。

## 总结

这篇文章写得非常有趣，希望你也喜欢阅读。我还有另一个关于RLHF局限性的部分——例如人类偏好中的偏见、评估挑战和数据所有权问题——但决定将其留到另一篇文章中，因为这篇文章已经很长了。

当我深入研究关于RLHF的论文时，有三点给我留下了深刻印象：

1. 训练像ChatGPT这样的模型是一个相当复杂的过程——它能够运行本身就令人惊讶。
2. 规模是疯狂的。我一直知道LLMs需要大量的数据和计算能力，但整个互联网的数据！？
3. 公司（过去）在分享其过程方面是多么慷慨。DeepMind的[Gopher](https://arxiv.org/abs/2112.11446)论文有120页。OpenAI的[InstructGPT](https://arxiv.org/abs/2203.02155)论文有68页，Anthropic分享了他们的161K hh-rlhf比较实例，Meta将其LLaMa模型用于研究。社区还有大量的善意和动力，致力于创建开源模型和数据集，如OpenAssistant和LAION。这是一个令人兴奋的时代！

我们仍处于LLMs的初期阶段。世界其他地区刚刚意识到LLMs的潜力，因此比赛才刚刚开始。关于LLMs的许多事情，包括RLHF，仍有待探讨。但我希望这篇文章能帮助你更好地理解LLMs在幕后是如何训练的，这有望帮助你选择最适合你需求的LLM！

## 论文

```
格式:
- [title](paper link) [links]
  - keyword
  - code
  - experiment environments and datasets
```

### 2023

- [GPT-4 Technical Report](https://cdn.openai.com/papers/gpt-4.pdf)
  - Keyword: A large-scale, multimodal model, Transformerbased model, Fine-tuned used RLHF
  - Code: [official](https://github.com/openai/evals)
  - Dataset: [DROP](https://allenai.org/data/drop), [WinoGrande](https://winogrande.allenai.org/), [HellaSwag](https://rowanzellers.com/hellaswag/), [ARC](https://allenai.org/data/arc), [HumanEval](https://github.com/openai/human-eval), [GSM8K](https://paperswithcode.com/dataset/gsm8k), [MMLU](https://paperswithcode.com/dataset/mmlu), [TruthfulQA](https://github.com/sylinrl/TruthfulQA)

- [RAFT: Reward rAnked FineTuning for Generative Foundation Model Alignment](https://arxiv.org/pdf/2304.06767.pdf)
  - Keyword: Alternative to PPO, ChatGPT, Diffusion Model
  - Code: [official](https://github.com/OptimalScale/LMFlow)

- [RRHF: Rank Responses to Align Language Models with Human Feedback without tears](https://arxiv.org/pdf/2304.05302v1.pdf)
  - Keyword: New paradigm for RLHF
  - Code: [official](https://github.com/GanjinZero/RRHF)

- [Few-shot Preference Learning for Human-in-the-Loop RL](https://openreview.net/pdf?id=IKC5TfXLuW0)
  - Keyword: Preference Learning, Interactive Learning, Multi-task Learning, Expanding the pool of available data by viewing human-in-the-loop RL
  - Code: [official](https://github.com/jhejna/few-shot-preference-rl)

- [Better Aligning Text-to-Image Models with Human Preference](https://arxiv.org/abs/2303.14420)
  - Keyword: Diffusion Model, Text-to-Image, Aesthetic
  - Code: [official](https://github.com/tgxs002/align_sd)
  
- [ImageReward: Learning and Evaluating Human Preferences for Text-to-Image Generation](https://arxiv.org/pdf/2304.05977v2.pdf)
  - Keyword: General-purpose text-to-Image human preference RM, Evaluating Text-to-Image Generative Models
  - Code: [official](https://github.com/THUDM/ImageReward)
  - Dataset: [COCO](https://cocodataset.org/#home), [DiffusionDB](https://poloclub.github.io/diffusiondb/)
  
- [Aligning Text-to-Image Models using Human Feedback](https://arxiv.org/pdf/2302.12192.pdf)
  - Keyword: Text-to-Image, Stable diffusion model, Reward function that predicts human feedback
  
- [Visual ChatGPT: Talking, Drawing and Editing with Visual Foundation Models](https://arxiv.org/pdf/2303.04671.pdf)
  - Keyword: Visual Foundation Models, Visual ChatGPT 
  - Code: [official](https://github.com/microsoft/visual-chatgpt)
  
- [Pretraining Language Models with Human Preferences](https://arxiv.org/abs/2302.08582) (PHF)
  - Keyword: Pretraining, offline RL, Decision transformer
  - Code: [official](https://github.com/tomekkorbak/pretraining-with-human-feedback)
  
- [Aligning Language Models with Preferences through f-divergence Minimization](https://arxiv.org/abs/2302.08215) (f-DPG)
  - Keyword: f-divergence, RL with KL penalties
  
- [Principled Reinforcement Learning with Human Feedback from Pairwise or K-wise Comparisons](https://arxiv.org/pdf/2301.11270.pdf)
  - Keyword: Pessimistic MLE, Max-entropy IRL
  
- [The Capacity for Moral Self-Correction in Large Language Models](https://arxiv.org/pdf/2302.07459.pdf)
  - Keyword: Improve moral self-correction capability by increasing RLHF training
  - Dataset; [BBQ](https://github.com/nyu-mll/BBQ)

### 2022

- [Is Reinforcement Learning (Not) for Natural Language Processing?: Benchmarks, Baselines, and Building Blocks for Natural Language Policy Optimization](https://arxiv.org/abs/2210.01241) (NLPO)
  - Keyword: Optimizing language generators with RL, Benchmark,  Performant RL algorithm
  - Code: [official](https://github.com/allenai/RL4LMs)
  - Dataset: [IMDB](https://www.imdb.com/interfaces/), [CommonGen](https://inklab.usc.edu/CommonGen/), [CNN Daily Mail](https://github.com/abisee/cnn-dailymail), [ToTTo](https://github.com/google-research-datasets/ToTTo), [WMT-16 (en-de)](https://www.statmt.org/wmt16/it-translation-task.html),[NarrativeQA](https://github.com/deepmind/narrativeqa), [DailyDialog](http://yanran.li/dailydialog)
- [Scaling Laws for Reward Model Overoptimization](https://arxiv.org/abs/2210.10760)
  - Keyword: Gold reward model train proxy reward model, Dataset size, Policy parameter size, BoN, PPO
- [Improving alignment of dialogue agents via targeted human judgements](https://arxiv.org/abs/2209.14375) (Sparrow)
  - Keyword: Information-seeking dialogue agent, Break down the good dialogue into natural language rules, DPC, Interact with the model to elicit violation of a specific rule (Adversarial Probing)
  - Dataset: [Natural Questions](https://ai.google.com/research/NaturalQuestions), [ELI5](https://facebookresearch.github.io/ELI5/), [QuALITY](https://github.com/nyu-mll/quality), [TriviaQA](http://nlp.cs.washington.edu/triviaqa/), [WinoBias](https://github.com/uclanlp/corefBias/tree/master/WinoBias/wino), [BBQ](https://github.com/nyu-mll/BBQ)
- [Red Teaming Language Models to Reduce Harms: Methods, Scaling Behaviors, and Lessons Learned](https://arxiv.org/abs/2209.07858)
  - Keyword: Red team language model, Investigate scaling behaviors, Read teaming Dataset
  - Code: [official](https://github.com/anthropics/hh-rlhf)
- [Dynamic Planning in Open-Ended Dialogue using Reinforcement Learning](https://arxiv.org/abs/2208.02294)
  - Keyword: Real-time, Open-ended dialogue system, Pairs the succinct embedding of the conversation state by language models, CAQL, CQL, [BERT](https://github.com/google-research/bert)
- [Quark: Controllable Text Generation with Reinforced Unlearning](https://arxiv.org/abs/2205.13636)
  - Keyword: Fine-tuning the language model on signals of what not to do, Decision Transformer, LLM tuning with PPO
  - Code: [official](https://github.com/gximinglu/quark)
  - Dataset: [WRITINGPROMPTS](https://www.kaggle.com/datasets/ratthachat/writing-prompts), [SST-2](https://huggingface.co/distilbert-base-uncased-finetuned-sst-2-english), [WIKITEXT-103](https://blog.salesforceairesearch.com/the-wikitext-long-term-dependency-language-modeling-dataset/)
- [Training a Helpful and Harmless Assistant with Reinforcement Learning from Human Feedback](https://arxiv.org/abs/2204.05862)
  - Keyword: Harmless assistants, Online mode, Robustness of RLHF training, OOD detection.
  - Code: [official](https://github.com/anthropics/hh-rlhf)
  - Dataset: [TriviaQA](http://nlp.cs.washington.edu/triviaqa/), [HellaSwag](https://rowanzellers.com/hellaswag/), [ARC](https://allenai.org/data/arc), [OpenBookQA](https://allenai.org/data/open-book-qa), [LAMBADA](https://zenodo.org/record/2630551#.Y_KLJ-yZNhF), [HumanEval](https://github.com/openai/human-eval), [MMLU](https://github.com/hendrycks/test), [TruthfulQA](https://github.com/sylinrl/TruthfulQA)
- [Teaching language models to support answers with verified quotes](https://arxiv.org/abs/2203.11147) (GopherCite)
  - Keyword: Generate answers which citing specific evidence, Abstain from answering when unsure
  - Dataset: [Natural Questions](https://ai.google.com/research/NaturalQuestions), [ELI5](https://facebookresearch.github.io/ELI5/), [QuALITY](https://github.com/nyu-mll/quality), [TruthfulQA](https://github.com/sylinrl/TruthfulQA)
- [Training language models to follow instructions with human feedback](https://arxiv.org/abs/2203.02155) (InstructGPT)
  - Keyword: Large Language Model, Align Language Model with Human Intent
  - Code: [official](https://github.com/openai/following-instructions-human-feedback)
  - Dataset: [TruthfulQA](https://github.com/sylinrl/TruthfulQA), [RealToxicityPrompts](https://allenai.org/data/real-toxicity-prompts)
- [Constitutional AI: Harmlessness from AI Feedback](https://arxiv.org/pdf/2212.08073.pdf)
  - Keyword: RL from AI feedback(RLAIF), Training a harmless AI assistant through selfimprovement, Chain-of-thought style, Control AI behavior more precisely
  - Code: [official](https://github.com/anthropics/ConstitutionalHarmlessnessPaper)
- [Discovering Language Model Behaviors with Model-Written Evaluations](https://arxiv.org/abs/2212.09251)
  - Keyword: Automatically generate evaluations with LMs, More RLHF makes LMs worse, LM-written evaluations are highquality
  - Code: [official](https://github.com/anthropics/evals)
  - Dataset: [BBQ](https://github.com/nyu-mll/BBQ), [Winogender Schemas](https://github.com/rudinger/winogender-schemas)
- [Non-Markovian Reward Modelling from Trajectory Labels via Interpretable Multiple Instance Learning](https://arxiv.org/abs/2205.15367)
  - Keyword: Reward Modelling (RLHF), Non-Markovian, Multiple Instance Learning, Interpretability
  - Code: [official](https://github.com/JAEarly/MIL-for-Non-Markovian-Reward-Modelling)

### 2021

- [WebGPT: Browser-assisted question-answering with human feedback](https://arxiv.org/abs/2112.09332) (WebGPT)
  - Reiichiro Nakano, Jacob Hilton, Suchir Balaji, et al.
  - Keyword: Model search the web and provide reference， Imitation learning， BC, long form question
  - Dataset: [ELI5](https://facebookresearch.github.io/ELI5/), [TriviaQA](http://nlp.cs.washington.edu/triviaqa/), [TruthfulQA](https://github.com/sylinrl/TruthfulQA)
- [Recursively Summarizing Books with Human Feedback](https://arxiv.org/abs/2109.10862)
  - Jeff Wu, Long Ouyang, Daniel M. Ziegler, Nisan Stiennon, Ryan Lowe, Jan Leike, Paul Christiano
  - Keyword:  Model trained on small task to assist human evaluate broader task, BC
  - Dataset: [Booksum](https://github.com/salesforce/booksum), [NarrativeQA](https://github.com/deepmind/narrativeqa)
- [Revisiting the Weaknesses of Reinforcement Learning for Neural Machine Translation](https://arxiv.org/abs/2106.08942)
  - Samuel Kiegeland, Julia Kreutzer
  - Keyword:  The success of policy gradient is because of reward rather than the shape of output distribution, Machine Translation, NMT, DOmain Adaption
  - Code: [official](https://github.com/samuki/reinforce-joey)
  - Dataset: [WMT15](https://www.statmt.org/wmt15/index.html), [IWSLT14](https://sites.google.com/site/iwsltevaluation2014/mt-track)

### 2020 年及之前

- [Learning to summarize from human feedback](https://arxiv.org/abs/2009.01325)
  - Nisan Stiennon, Long Ouyang, Jeff Wu, Daniel M. Ziegler, Ryan Lowe, Chelsea Voss, Alec Radford, Dario Amodei, Paul Christiano
  - Keyword: Care about summary quality, Training loss affect the model behavior, Reward model generalizes to new datasets
  - Code: [official](https://github.com/openai/summarize-from-feedback)
  - Dataset: [TL;DR](https://www.tensorflow.org/datasets/catalog/reddit), [CNN/DM](https://github.com/abisee/cnn-dailymail)
- [Fine-Tuning Language Models from Human Preferences](https://arxiv.org/abs/1909.08593)
  - Daniel M. Ziegler, Nisan Stiennon, Jeffrey Wu, Tom B. Brown, Alec Radford, Dario Amodei, Paul Christiano, Geoffrey Irving
  - Keyword: Reward learning for language, Continuing text with positive sentiment, Summary task, Physical descriptive
  - Code: [official](https://github.com/openai/lm-human-preferences)
  - Dataset: [TL;DR](https://www.tensorflow.org/datasets/catalog/reddit), [CNN/DM](https://github.com/abisee/cnn-dailymail)
- [Scalable agent alignment via reward modeling: a research direction](https://arxiv.org/abs/1811.07871)
  - Jan Leike, David Krueger, Tom Everitt, Miljan Martic, Vishal Maini, Shane Legg
  - Keyword: Agent alignment problem, Learn reward from interaction, Optimize reward with RL, Recursive reward modeling
  - Code: [official](https://github.com/rddy/ReQueST)
  - Env: Atari
- [Reward learning from human preferences and demonstrations in Atari](https://arxiv.org/abs/1811.06521)
  - Borja Ibarz, Jan Leike, Tobias Pohlen, Geoffrey Irving, Shane Legg, Dario Amodei
  - Keyword: Expert demonstration trajectory preferences reward hacking problem, Noise in human label
  - Code: [official](https://github.com/rddy/ReQueST)
  - Env: Atari
- [Deep TAMER: Interactive Agent Shaping in High-Dimensional State Spaces](https://arxiv.org/abs/1709.10163)
  - Garrett Warnell, Nicholas Waytowich, Vernon Lawhern, Peter Stone
  - Keyword:  High dimension state, Leverage the input of Human trainer
  - Code: [third party](https://github.com/bharadwaj1098/Tamer)
  - Env: Atari
- [Deep reinforcement learning from human preferences](https://arxiv.org/abs/1706.03741)
  - Paul Christiano, Jan Leike, Tom B. Brown, Miljan Martic, Shane Legg, Dario Amodei
  - Keyword: Explore goal defined in human preferences between pairs of trajectories segmentation, Learn more complex thing than human feedback
  - Code: [official](https://github.com/mrahtz/learning-from-human-preferences)
  - Env: Atari, MuJoCo
- [Interactive Learning from Policy-Dependent Human Feedback](https://arxiv.org/abs/1701.06049)
  - James MacGlashan, Mark K Ho, Robert Loftin, Bei Peng, Guan Wang, David Roberts, Matthew E. Taylor, Michael L. Littman
  - Keyword: Decision is influenced by current policy rather than human feedback, Learn from policy dependent feedback that converges to a local optimal

## 代码库

```
格式:
- [title](codebase link) [links]
  - keyword
  - experiment environments, datasets or tasks
```

- [PaLM + RLHF - Pytorch](https://github.com/lucidrains/PaLM-rlhf-pytorch)
  - Keyword: Transformers, PaLM architecture
  - Dataset: [enwik8](http://prize.hutter1.net/)
- [lm-human-preferences](https://github.com/openai/lm-human-preferences)
  - Keyword: Reward learning for language, Continuing text with positive sentiment, Summary task, Physical  descriptive
  - Dataset: [TL;DR](https://www.tensorflow.org/datasets/catalog/reddit), [CNN/DM](https://github.com/abisee/cnn-dailymail)
- [following-instructions-human-feedback](https://github.com/openai/following-instructions-human-feedback)
  - Keyword: Large Language Model, Align Language Model with Human Intent
  - Dataset: [TruthfulQA](https://github.com/sylinrl/TruthfulQA) [RealToxicityPrompts](https://allenai.org/data/real-toxicity-prompts)
- [Transformer Reinforcement Learning (TRL)](https://github.com/lvwerra/trl)
  - Keyword: Train LLM with RL, PPO, Transformer
  - Task: [IMDB sentiment](https://www.imdb.com/interfaces/)
- [Transformer Reinforcement Learning X (TRLX)](https://github.com/CarperAI/trlx)
  - Keyword: Distributed training framework, T5-based language models, Train LLM with RL, PPO, ILQL
  - Task: Fine tuning LLM with RL using provided reward function or reward-labeled dataset
- [RL4LMs (A modular RL library to fine-tune language models to human preferences)](https://github.com/allenai/RL4LMs)
  - Keyword: Optimizing language generators with RL, Benchmark,  Performant RL algorithm
  - Dataset: [IMDB](https://www.imdb.com/interfaces/), [CommonGen](https://inklab.usc.edu/CommonGen/), [CNN Daily Mail](https://github.com/abisee/cnn-dailymail), [ToTTo](https://github.com/google-research-datasets/ToTTo), [WMT-16 (en-de)](https://www.statmt.org/wmt16/it-translation-task.html), [NarrativeQA](https://github.com/deepmind/narrativeqa), [DailyDialog](http://yanran.li/dailydialog)
- [HH-RLHF](https://github.com/anthropics/hh-rlhf)
  - Keyword: Human preference dataset, Red teaming data, machine-written
  - Task: Open-source dataset for human preference data about helpfulness and harmlessness
- [LaMDA-rlhf-pytorch](https://github.com/conceptofmind/LaMDA-rlhf-pytorch)
  - Keyword: LaMDA, Attention-mechanism
  - Task: Open-source pre-training implementation of Google's LaMDA research paper in PyTorch
- [TextRL](https://github.com/voidful/TextRL)
  - Keyword: huggingface's transformer
  - Task: Text generation
  - Env: PFRL, gym
- [minRLHF](https://github.com/thomfoster/minRLHF)
  - Keyword: PPO, Minimal library
  - Task: educational purposes
- [Stanford Human Preferences Dataset(SHP)](https://huggingface.co/datasets/stanfordnlp/SHP)
  - Keyword: Naturally occurring and human-written dataset,18 different subject areas
  - Task: Intended to be used for training RLHF reward models 
- [PromptSource](https://github.com/bigscience-workshop/promptsource)
  - Keyword: Prompted English datasets,  Mapping a data example into natural language
  - Task:  Toolkit for creating, Sharing and using natural language prompts
- [Structured Knowledge Grounding(SKG) Resources Collections](https://unifiedskg.com/)
  - Keyword: Structured Knowledge Grounding
  - Task:  Collection of datasets are related to structured knowledge grounding
- [The Flan Collection](https://github.com/google-research/FLAN/tree/main/flan/v2)
  - Task: Collection compiles datasets from Flan 2021, P3, Super-Natural Instructions


## 博客

- [OpenAI] [ChatGPT: Optimizing Language Models for Dialogue](https://openai.com/blog/chatgpt)
- [Hugging Face] [Illustrating Reinforcement Learning from Human Feedback (RLHF)](https://huggingface.co/blog/rlhf)
- [知乎] [通向AGI之路：大型语言模型 (LLM) 技术精要](https://zhuanlan.zhihu.com/p/597586623)
- [知乎] [大语言模型的涌现能力：现象与解释](https://zhuanlan.zhihu.com/p/621438653)
- [W&B Fully Connected][ Understanding Reinforcement Learning from Human Feedback (RLHF)](https://wandb.ai/ayush-thakur/RLHF/reports/Understanding-Reinforcement-Learning-from-Human-Feedback-RLHF-Part-1--VmlldzoyODk5MTIx)
- [Deepmind] [Learning through human feedback](https://www.deepmind.com/blog/learning-through-human-feedback)
- [Notion] [深入理解语言模型的突现能力](https://yaofu.notion.site/514f4e63918749398a1a8a4c660e0d5b)
- [Notion] [拆解追溯 GPT-3.5 各项能力的起源](https://yaofu.notion.site/GPT-3-5-360081d91ec245f29029d37b54573756#cf00f4e11d974187956122ce7d534386)
- [gist] [Reinforcement Learning for Language Models](https://gist.github.com/yoavg/6bff0fecd65950898eba1bb321cfbd81)
- [YouTube] [John Schulman - Reinforcement Learning from Human Feedback: Progress and Challenges](https://www.youtube.com/watch?v=hhiLw5Q_UFg)

## GPT-4

### 什么是RLHF

> 人类反馈强化学习 (RLHF) 是一种将强化学习 (RL) 技术与人类反馈相结合以训练 AI 代理的方法。目标是创建可以从人类生成的数据（例如演示、评估甚至更正）中学习的人工智能系统，以更有效、更准确地执行任务。
>
> 在传统的强化学习中，代理通过与环境交互并根据其行为接收奖励或惩罚形式的反馈来学习。然而，设计一个好的奖励函数可能很困难，有时所需的行为很难定义或量化。
> 借助 RLHF，AI 代理会收到来自人类培训师的反馈，他们可以提供额外的信息或指导。此反馈可用于创建更好的奖励功能或在学习过程中提供额外的监督。有多种方法可以将人类反馈纳入学习过程，例如： 
>
> 1. 模仿学习：AI 代理通过观察人类对任务的演示来学习，并尝试模仿观察到的行为。
> 2. 交互式反馈：AI 代理在执行任务时实时接收来自人类的反馈。这可以是更正、建议或强化信号的形式。
> 3. 排名或比较：AI 代理被赋予多个轨迹或动作序列，人类训练员根据他们的偏好或质量对它们进行排名。然后，代理学习更喜欢排名更高的动作。
>
> 从人类反馈中强化学习可以带来更高效和准确的人工智能系统，因为它利用人类知识和专业知识来指导学习过程。然而，它也带来了挑战，例如结合嘈杂或有偏见的人类反馈，以及确保人工智能系统能够很好地泛化到新情况。

### 怎样学习RLHF

> 您可以遵循几个步骤来学习和实施 RLHF： 
>
> 1. 学习强化学习的基础知识：
>
>    在深入学习 RLHF 之前，了解强化学习 (RL) 的基础知识至关重要。一些入门资源包括： 
>
>    - Richard S. Sutton 和 Andrew G. Barto 的“强化学习：简介”（教科书）
>    - OpenAI 的“Spinning Up in Deep RL”（在线资源）：https://spinningup.openai.com/en/latest/
>    - Sergey Levine 的“深度强化学习”课程（YouTube）：https://www.youtube.com/playlist?list=PL_iWQOsE6TfURIIhCrlt-wj9ByIVpbfGc
>
> 2. 了解人类反馈在 RL 中的作用：熟悉如何将人类反馈集成到 RL 框架中。研究不同类型的人类反馈，例如演示、交互式反馈以及排名或比较。
>
> 3. 了解现有的 RLHF 算法：有几种专门为 RLHF 设计的算法。其中一些包括： 
>
>    - DAgger（数据集聚合）：一种从专家演示中学习的模仿学习算法。
>    - Deep Q-Learning from Demonstrations (DQfD)：一种结合了演示和传统 RL 的深度强化学习算法。
>    - COACH（CORrective Advice Communicated by Humans）：一种基于交互式反馈的强化学习算法。
>
> 4. 选择合适的 RL 库和仿真环境：有几个库可以帮助您实现 RLHF 算法，例如：
>
>    - TensorFlow (Python)：https://www.tensorflow.org/
>    - PyTorch (Python)：https://pytorch.org/ 
>    - Stable Baselines (Python): https://github.com/hill-a/stable-baselines 
>
>    选择一个模拟环境来测试和评估你的 RLHF 实现，比如 OpenAI 的 Gym (https://gym.openai.com/), DeepMind 的Control Suite (https://github.com/deepmind/dm_control)，或 Unity ML-Agents (https://github.com/Unity-Technologies/ml-agents)。
>
> 5. 实施和试验 RLHF 算法：
>
>    一旦您对 RLHF 和必要的工具有了很好的理解，就可以开始实施和试验 RLHF 算法。以各种方式应用人工反馈并评估它对代理人的学习和绩效的影响。
>
> 6. 评估和完善您的方法：通过将其与其他 RLHF 方法或已建立的基线进行比较，不断评估和完善您的实施。分析您的方法的优点和缺点，并迭代以提高其性能。
>
> 请记住，学习和实施 RLHF 是一个持续的过程，需要时间和奉献精神。要有耐心，不断从可用资源中学习，并毫不犹豫地向强化学习社区中的其他人寻求帮助或指导。

### 自动驾驶领域如何利用RLHF增强安全决策

> **A1:**
>
> 人类反馈强化学习 (RLHF) 可以应用于自动驾驶领域，通过利用人类的专业知识和知识来增强安全决策。以下是在开发更安全的自动驾驶系统时使用 RLHF 的高级方法：
>
> 1. 定义问题：确定您想要改进的特定安全相关决策或自动驾驶方面。例如，这可能是避免碰撞、变道或适应不同的交通状况。
> 2. 收集人类示范：从人类司机那里获取驾驶数据，重点关注您想要增强的安全方面。数据应包括传感器输入、车辆状态和相应的人类行为。您可以使用公共数据集，例如 Waymo Open Dataset (https://waymo.com/open/) 或 ApolloScape (http://apolloscape.auto/)，或收集您自己的数据。
> 3. 预处理和注释数据：清理收集的数据并为您的 RL 模型提取相关特征。这可能涉及传感器融合、降噪或准备数据所需的任何其他预处理步骤。您可能还需要使用其他信息对数据进行注释，例如与安全相关的事件或人工反馈。
> 4. 实施 RLHF 算法：根据您收集的人类反馈类型选择合适的 RLHF 算法。这可能是一种模仿学习算法，如 DAgger，或者是演示和传统 RL 的组合，如 Deep Q-Learning from Demonstrations (DQfD)。
> 5. 训练 RL 代理：使用人类演示和反馈训练 RL 代理。根据算法的不同，这可能涉及从演示中进行监督学习、从交互式反馈中学习或从排序的动作序列中学习。
> 6. 使用额外的反馈进行微调：初始训练后，您可能希望通过收集更多的人工反馈来微调模型。这可能涉及让人类专家评估代理在模拟环境中的表现，提供纠正建议或对不同的动作序列进行排序。使用此附加反馈进一步完善模型并改进其安全决策。
> 7. 测试和验证模型：评估基于 RLHF 的自动驾驶系统在各种模拟场景或受控的真实环境中的性能。将其性能与其他方法和已建立的安全基线进行比较，并分析人类反馈对系统决策的影响。
> 8. 迭代和改进：根据评估结果，确定需要改进的地方，并改进 RLHF 方法。这可能涉及收集更多或质量更好的人类反馈、调整算法或更新模拟环境。
>
> 通过将人类反馈纳入自动驾驶系统的开发中，您可以利用人类专业知识来指导学习过程并加强安全决策。但是，重要的是要意识到人类反馈中的潜在偏差，并确保 RL 代理能够很好地泛化到新情况。
>
> **A2:**
>
> 以下是将人类反馈强化学习 (RLHF) 应用于自动驾驶领域的更多示例： 
>
> 1. 变道和并道：RLHF 可用于通过学习人类示范或反馈来改进变道和并道决策。可以训练自动驾驶汽车确定最佳变道时间，考虑周围车辆的位置和速度，并确保平稳安全的过渡。
> 2. 自适应巡航控制：基于 RLHF 的系统可用于开发自适应巡航控制算法，在适应交通流量的同时与前方车辆保持安全距离。通过从人类示范或反馈中学习，该算法可以更好地了解如何对不同的交通状况做出反应，并确保更舒适、更安全的驾驶体验。
> 3. 十字路口处理：处理十字路口对于自动驾驶车辆来说可能具有挑战性，尤其是在处理交通信号灯、停车标志和让行其他车辆时。 RLHF 方法可以通过学习人类驾驶员的决策和行为来帮助训练自动驾驶车辆安全高效地通过十字路口。
> 4. 行人和骑车人的检测和互动：RLHF 可用于改善行人和骑车人的检测和互动。自动驾驶汽车可以从人类反馈中学习，以更好地预测行人和骑自行车者的行为，确保在城市环境中进行更安全、更顺畅的交互。
> 5. 紧急机动：RLHF 可用于训练自动驾驶车辆进行紧急机动，例如突然制动或规避转向。通过从人类示范或反馈中学习，车辆可以制定更有效的策略来处理意外情况、最大限度地降低风险并避免碰撞。
> 6. 驾驶风格个性化：不同的驾驶员可能对驾驶风格有不同的偏好，例如平稳性、激进性或能源效率。 RLHF 可用于通过学习人类反馈或演示来使自动驾驶系统适应个人偏好，从而带来更加个性化和令人满意的驾驶体验。
>
> 这些示例展示了 RLHF 如何应用于自动驾驶的各个方面，以提高安全性、效率和用户体验。通过利用人类的专业知识和知识，RLHF 使自动驾驶汽车能够学习更好的策略并做出更明智的决策，最终实现更安全、更可靠的运行。

### 关于RLHF应用到自动驾驶的一些研究

> 1. "Learning from Demonstration for Autonomous Navigation in Complex Unstructured Terrain" by Ross et al. (2013) Link: https://ieeexplore.ieee.org/document/6563726 This paper presents an approach using the DAgger algorithm (Dataset Aggregation) to learn from expert demonstrations for off-road autonomous navigation.
> 2. "End-to-End Driving via Conditional Imitation Learning" by Codevilla et al. (2018) Link: https://arxiv.org/abs/1710.02410 This paper presents an end-to-end approach to learning a driving policy from human demonstrations using conditional imitation learning. The approach allows an autonomous vehicle to learn to drive in complex urban environments by imitating human demonstrations.
> 3. "ChauffeurNet: Learning to Drive by Imitating the Best and Synthesizing the Worst" by Bansal et al. (2018) Link: https://arxiv.org/abs/1812.03079 This work by Waymo researchers introduces ChauffeurNet, a system that learns to drive by imitating human driving data and synthesizing challenging situations. The model is trained using a combination of supervised learning from demonstrations and data augmentation with synthesized scenarios.
> 4. "Deep Imitative Models for Flexible Inference, Planning, and Control" by Brown et al. (2020) Link: https://arxiv.org/abs/1810.06544 This paper presents deep imitative models (DIMs) that learn to imitate expert demonstrations and generate safe, goal-directed behavior. The authors show that DIMs can be used for real-time planning and control in the context of autonomous driving.
> 5. "Safe Reinforcement Learning from Human Feedback for Urban Autonomous Driving" by Xuankun et al. (2021) Link: https://arxiv.org/abs/2103.15361 This paper investigates using human feedback in the form of safety rankings to train a safe reinforcement learning agent for urban autonomous driving. The authors propose an approach that combines demonstrations and safety rankings to train an RL agent with better safety performance.
> 6. "Deep Reinforcement Learning for Autonomous Driving with Demonstrations" by Matiisen et al. (2018) Link: https://arxiv.org/abs/1807.11646 This paper explores the use of deep reinforcement learning (DRL) with demonstrations for autonomous driving. The authors propose an approach that combines DRL with human driving demonstrations to improve the agent's performance, using a combination of imitation learning and policy optimization.
> 7. "Integrating Kinesthetic Teaching and Imitation Learning for Robust Autonomous Driving" by Jain et al. (2019) Link: https://arxiv.org/abs/1910.14254 This paper investigates the integration of kinesthetic teaching, a form of human feedback, with imitation learning for autonomous driving. The authors demonstrate that their approach enables a more robust driving policy that can handle challenging scenarios.
> 8. "CILRS: Learning to Drive from Human Feedback with Conditional Imitation Learning and Reward Shaping" by Li et al. (2020) Link: https://arxiv.org/abs/2006.10429 This paper proposes an approach called CILRS that combines conditional imitation learning and reward shaping to learn driving policies from human feedback. The authors demonstrate improved performance in simulation environments compared to baseline methods.
> 9. "Human-Guided Reinforcement Learning for Autonomous Driving: A Review" by Liu et al. (2021) Link: https://arxiv.org/abs/2109.14741 This is a review paper that discusses the current state of research on human-guided reinforcement learning for autonomous driving. The paper highlights the challenges and opportunities in the field and provides a comprehensive overview of various RLHF techniques applied to autonomous driving.
> 10. "A Survey of Deep Reinforcement Learning for Autonomous Driving" by Liu et al. (2021) Link: https://arxiv.org/abs/2109.10864 Although not focused exclusively on RLHF, this survey paper provides a thorough overview of deep reinforcement learning techniques applied to autonomous driving, including some that involve human feedback. The paper discusses different aspects of autonomous driving, such as perception, planning, and control, and how DRL methods can be applied to these areas.
> 11. "Way Off-Policy Batch Deep Reinforcement Learning of Implicit Human Preferences in Dialog" by Zhao et al. (2019) Link: https://arxiv.org/abs/1907.00456 Although not strictly focused on autonomous driving, this paper presents an interesting application of RLHF in learning human preferences in dialog systems. The techniques discussed in this work, such as off-policy learning and implicit preference learning, could potentially be applied to autonomous driving as well.
> 12. "Learning to Drive in a Day" by Kendall et al. (2018) Link: https://arxiv.org/abs/1807.00412 This paper presents a method for training a self-driving car using reinforcement learning in simulation and then transferring the learned policy to a real vehicle. While the paper does not directly focus on human feedback, it provides insights into training RL agents for autonomous driving that could be combined with human feedback techniques.
> 13. "SafeDRL: Safe Deep Reinforcement Learning for Autonomous Vehicles" by Ahn et al. (2020) Link: https://arxiv.org/abs/2003.08720 This paper presents SafeDRL, a method for training safe deep reinforcement learning agents for autonomous vehicles. The authors propose a multi-objective optimization framework to ensure safe operation while maximizing driving performance. Although human feedback is not explicitly incorporated, the paper provides useful insights into designing safe RL agents for autonomous driving.
> 14. "Deep Reinforcement Learning-based Vehicle Following with Semantic Segmentation" by Kim et al. (2020) Link: https://arxiv.org/abs/2006.00812 This paper presents a method for training an RL agent for vehicle following using semantic segmentation as input. While it does not directly focus on human feedback, the approach could potentially be combined with RLHF techniques to improve driving performance.
>
> ---
>
> As an AI language model, I have a knowledge cutoff in September 2021, so I am unable to provide you with the most recent research papers published after that date. However, you can easily find the latest research in the field by following a few steps:
>
> 1. Visit research platforms and repositories such as:
>    - arXiv (https://arxiv.org/)
>    - Google Scholar (https://scholar.google.com/)
>    - ResearchGate (https://www.researchgate.net/)
>    - IEEE Xplore (https://ieeexplore.ieee.org/)
> 2. Use relevant keywords and search queries to find the research papers you are interested in, such as:
>    - "Reinforcement Learning from Human Feedback for Autonomous Driving"
>    - "RLHF in Autonomous Driving"
>    - "Human-in-the-loop Reinforcement Learning for Self-driving Cars"
>    - "Imitation Learning for Autonomous Vehicles"
> 3. To get the most recent papers, you can filter or sort the search results by date or relevance, depending on the platform you are using.
> 4. Keep an eye on conferences and journals in the fields of autonomous driving, robotics, and reinforcement learning, such as:
>    - IEEE Intelligent Vehicles Symposium (IV)
>    - IEEE Conference on Intelligent Transportation Systems (ITSC)
>    - Conference on Robot Learning (CoRL)
>    - Advances in Neural Information Processing Systems (NeurIPS)
>    - International Conference on Learning Representations (ICLR)
>
> By following these steps, you can stay updated on the latest research and advancements in applying RLHF to the field of autonomous driving.
