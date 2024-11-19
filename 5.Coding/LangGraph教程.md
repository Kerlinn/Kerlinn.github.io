# LangChain Academy

> 课程链接：https://academy.langchain.com/courses/intro-to-langgraph

## Introduction to LangGraph

了解 LangGraph（我们用于构建agent和multi-agent应用程序的框架）的基础知识。与 LangChain 软件包不同，LangGraph 可帮助开发人员在agent工作流程中添加更好的精度和控制。

### 介绍

欢迎来到 LangChain Academy 的 LangGraph 入门课程！本课程分为五个模块，从基础知识开始，逐渐发展到更高级的主题。

每个模块都包含视频课程，可引导您了解关键概念以及相应的notebook。您还可以在每个模块中找到一个 **studio** 子目录，其中包含一组相关图表，我们将使用 LangGraph API 和 Studio 来探索这些图表。

### 设置

以下是我们推荐的入门课程设置。我们将使用[此处](https://github.com/langchain-ai/langchain-academy)的笔记本集。如果您更喜欢手动下载笔记本，可以[在此处](https://github.com/langchain-ai/langchain-academy/archive/refs/heads/main.zip)访问 ZIP 文件。每个模块还将包含指向相应笔记本的链接，以及用于在 Google Colab 中访问它们的其他选项以快速入门。

### Python 版本

要充分利用本课程，请确保您使用的是 Python 3.11。此版本是与 LangGraph 的最佳兼容性所必需的。如果您使用的是旧版本，升级将确保一切顺利进行。

```shell
python3 --version
```

### 克隆存储库

```shell
git clone https://github.com/langchain-ai/langchain-academy.git
$ cd langchain-academy
```

### 创建环境并安装依赖项

```shell
$ python3 -m venv lc-academy-env
$ source lc-academy-env/bin/activate
$ pip install -r requirements.txt
```

### 运行 notebook

如果您尚未设置 Jupyter，请按照[此处的](https://jupyter.org/install)安装说明进行操作。

```shell
$ jupyter notebook
```



## Module 0：Overview

### Context

在 LangChain，我们的目标是让构建 LLM。您可以构建的一种 LLM 应用程序是agent。构建agent有很多令人兴奋的事情，因为它们可以自动执行以前不可能完成的各种任务。

但在实践中，构建能够可靠地执行这些任务的系统非常困难。随着我们与用户合作将agent投入生产，我们了解到通常需要更多的控制。您可能需要agent始终先调用特定工具，或根据其状态使用不同的提示。

为了解决这个问题，我们构建了 [LangGraph](https://langchain-ai.github.io/langgraph/)——一个用于构建agent和多agent应用程序的框架。与 LangChain 包不同，LangGraph 的核心设计理念是帮助开发人员在 Agent 工作流中增加更好的精度和控制力，以适应现实世界系统的复杂性。

### 课程结构

该课程由一组模块组成，每个模块都侧重于与 LangGraph 相关的特定主题。您将看到每个模块的文件夹，其中包含一系列笔记本。每个笔记本都将附带一个视频，以帮助了解概念，但笔记本也是独立的，这意味着它们包含说明，可以独立于视频进行查看。每个模块文件夹还包含一个 `studio` 文件夹，其中包含一组可以加载到 [LangGraph Studio](https://github.com/langchain-ai/langgraph-studio) 中的graphs，LangGraph Studio是我们用于构建 LangGraph 应用程序的 IDE。

### Chat Models

在本课程中，我们将使用[chat models](https://python.langchain.com/v0.2/docs/concepts/#chat-models)，它执行一些操作，将一系列消息作为输入，并将聊天消息作为输出返回。LangChain 不托管任何聊天模型，而是依赖第三方集成。[这是](https://python.langchain.com/v0.2/docs/integrations/chat/) LangChain 中的第三方聊天模型集成列表！默认情况下，该课程将使用 [ChatOpenAI](https://python.langchain.com/v0.2/docs/integrations/chat/openai/)，因为它既受欢迎又高性能。如前所述，请确保您有 `OPENAI_API_KEY`。

让我们检查您的`OPENAI_API_KEY`是否已设置，如果没有，系统会要求您输入。

```shell
%%capture --no-stderr
%pip install --quiet -U langchain_openai langchain_core langchain_community tavily-python
```

```python
import os, getpass

def _set_env(var: str):
    if not os.environ.get(var):
        os.environ[var] = getpass.getpass(f"{var}: ")

_set_env("OPENAI_API_KEY")
```

[以下是](https://python.langchain.com/v0.2/docs/how_to/#chat-models)您可以使用聊天模型执行的所有操作的有用操作，但我们将在下面展示一些亮点。如果您已按照 README 中的说明运行 `pip install -r requirements.txt` ，则您已安装 `langchain-openai` 包。有了这个，我们可以实例化我们的 `ChatOpenAI` 模型对象。如果您是第一次注册 API，您应该会收到可应用于任何模型[的免费积分](https://community.openai.com/t/understanding-api-limits-and-free-tier/498517)。您可以[在此处](https://openai.com/api/pricing/)查看各种型号的定价。笔记本电脑将默认使用 `gpt-4o`，因为它在质量、价格和速度之间取得了很好的平衡，[在这里查看更多](https://help.openai.com/en/articles/7102672-how-can-i-access-gpt-4-gpt-4-turbo-gpt-4o-and-gpt-4o-mini)，但您也可以选择价格较低的 `gpt-3.5` 系列型号。

我们可以使用聊天模型设置[一些标准参数](https://python.langchain.com/v0.2/docs/concepts/#chat-models)。其中最常见的两种是：

- `model`：模型的名称
- `temperature`：采样温度

`温度` 控制模型输出的随机性或创造性，其中低温 （接近 0） 的输出更具**确定性和集中性**。这适用于需要准确性或事实响应的任务。高温（接近 1）适用于**创造性任务或产生不同的响应**。

```python
from langchain_openai import ChatOpenAI
gpt4o_chat = ChatOpenAI(model="gpt-4o", temperature=0)
gpt35_chat = ChatOpenAI(model="gpt-3.5-turbo-0125", temperature=0)
```

LangChain 中的聊天模型有很多[默认方法](https://python.langchain.com/v0.2/docs/concepts/#runnable-interface)。在大多数情况下，我们将使用：

- `stream`：流回响应的块
- `invoke`：在 input 上调用链

而且，如前所述，聊天模型将[消息](https://python.langchain.com/v0.2/docs/concepts/#messages)作为输入。消息具有 role （描述消息的发布者） 和 content 属性。我们稍后会详细讨论这个问题，但在这里我们只展示基础知识。

```python
from langchain_core.messages import HumanMessage

# Create a message
msg = HumanMessage(content="Hello world", name="Lance")

# Message list
messages = [msg]

# Invoke the model with a list of messages 
gpt4o_chat.invoke(messages)
```

```python
AIMessage(content='Hello! How can I assist you today?', additional_kwargs={'refusal': None}, response_metadata={'token_usage': {'completion_tokens': 9, 'prompt_tokens': 11, 'total_tokens': 20}, 'model_name': 'gpt-4o-2024-05-13', 'system_fingerprint': 'fp_157b3831f5', 'finish_reason': 'stop', 'logprobs': None}, id='run-d3c4bc85-ef14-49f6-ba7e-91bf455cffee-0', usage_metadata={'input_tokens': 11, 'output_tokens': 9, 'total_tokens': 20})
```

我们收到 `AIMessage` 响应。另外，请注意，我们只能使用字符串调用 chat 模型。当字符串作为输入传入时，它会转换为 `HumanMessage`，然后传递给底层模型。

```python
gpt4o_chat.invoke("hello world")
# AIMessage(content='Hello! How can I assist you today?', additional_kwargs={'refusal': None}, response_metadata={'token_usage': {'completion_tokens': 9, 'prompt_tokens': 9, 'total_tokens': 18}, 'model_name': 'gpt-4o-2024-05-13', 'system_fingerprint': 'fp_157b3831f5', 'finish_reason': 'stop', 'logprobs': None}, id='run-d6f6b682-e29a-44de-b45e-79fad1e405e5-0', usage_metadata={'input_tokens': 9, 'output_tokens': 9, 'total_tokens': 18})
```


```python
gpt35_chat.invoke("hello world")
# AIMessage(content='Hello! How can I assist you today?', additional_kwargs={'refusal': None}, response_metadata={'token_usage': {'completion_tokens': 9, 'prompt_tokens': 9, 'total_tokens': 18}, 'model_name': 'gpt-3.5-turbo-0125', 'system_fingerprint': None, 'finish_reason': 'stop', 'logprobs': None}, id='run-c75d3f0f-2d71-47be-b14c-42b8dd2b4b08-0', usage_metadata={'input_tokens': 9, 'output_tokens': 9, 'total_tokens': 18})
```

该界面在所有聊天模型中都是一致的，并且模型通常在每个笔记本启动时初始化一次。

因此，如果您非常喜欢其他提供程序，则无需更改下游代码即可在模型之间轻松切换。

### Search Tools

您还将在 README 中看到 [Tavily](https://tavily.com/)，这是一个针对 LLMs，旨在提供高效、快速和持久的搜索结果。如前所述，它很容易注册并提供慷慨的免费套餐。一些课程（在模块 4 中）将默认使用 Tavily，但如果您想自己修改代码，当然也可以使用其他搜索工具。

```python
_set_env("TAVILY_API_KEY")
```

```python
from langchain_community.tools.tavily_search import TavilySearchResults
tavily_search = TavilySearchResults(max_results=3)
search_docs = tavily_search.invoke("What is LangGraph?")
```

```python
search_docs
```

```python
[{'url': 'https://www.datacamp.com/tutorial/langgraph-tutorial',
  'content': 'LangGraph is a library within the LangChain ecosystem designed to tackle these challenges head-on. LangGraph provides a framework for defining, coordinating, and executing multiple LLM agents (or chains) in a structured manner.'},
 {'url': 'https://langchain-ai.github.io/langgraph/',
  'content': 'Overview LangGraph is a library for building stateful, multi-actor applications with LLMs, used to create agent and multi-agent workflows. Compared to other LLM frameworks, it offers these core benefits: cycles, controllability, and persistence. LangGraph allows you to define flows that involve cycles, essential for most agentic architectures, differentiating it from DAG-based solutions. As a ...'},
 {'url': 'https://www.youtube.com/watch?v=nmDFSVRnr4Q',
  'content': 'LangGraph is an extension of LangChain enabling Multi-Agent conversation and cyclic chains. This video explains the basics of LangGraph and codesLangChain in...'}]
```

## Module 1：Introduction

### LangGraph 常见问题

- 我需要使用 LangChain 才能使用 LangGraph 吗？有什么区别？

> 不。LangGraph 是一个针对复杂agent系统的编排框架，比 LangChain agent更底层、可控。另一方面，LangChain 提供了一个标准接口来与模型和其他组件进行交互，这对于直接的链和检索流很有用。·

- LangGraph 与其他agent框架有何不同？

> 其他agent框架可以用于简单的通用任务，但无法满足根据公司需求定制的复杂任务。LangGraph 提供了一个更具表现力的框架来处理公司的独特任务，而不会将用户限制在单个黑盒认知架构中。

- LangGraph 会影响我的应用程序的性能吗？

> LangGraph 不会为您的代码增加任何开销，并且专为流式工作流而设计。

- LangGraph 是开源的吗？这是免费的吗？

> 是的。LangGraph 是 MIT 许可的开源库，可以免费使用。

- LangGraph Cloud 是开源的吗？

> 不。[LangGraph Cloud](https://langchain-ai.github.io/langgraph/cloud/) 是专有软件，最终将成为某些使用层级的付费服务。在对服务收费之前，我们始终会提前通知，并以优惠的价格奖励我们的早期采用者。

- 如何启用 LangGraph Cloud？

> 目前，LangGraph Cloud 还处于 beta 阶段。在测试版期间，所有使用 Plus 和 Enterprise 计划的 LangSmith 用户都可以访问 LangGraph Cloud。查看[文档](https://langchain-ai.github.io/langgraph/cloud/)。

- LangGraph 和 LangGraph Cloud 有何不同？

> LangGraph 是一个有状态的编排框架，可为agent工作流带来更多控制。LangGraph Cloud 是一项用于部署和扩展 LangGraph 应用程序的服务，内置了用于原型设计、调试和共享 LangGraph 应用程序的 Studio。如果您想了解更多信息，请查看[本页](https://www.langchain.com/langgraph)底部常见问题解答中的比较表。

- LangGraph 如何融入 LangChain 生态系统？

> 我们的目标是简化 LLM
>
> **Development**：使用 LangChain 的开源构建块、组件和第三方集成构建您的应用程序。使用 LangGraph 构建具有一流流式处理和人机回圈支持的有状态agent。
>
> **Production**：使用 LangSmith 检查、监控和评估您的链，以便您可以放心地持续优化和部署。
>
> **Deployment**：使用 LangGraph Cloud，将您的 LangGraph 应用程序转换为生产就绪型 API 和助手。
>
> ![image-20240921142940641](./LangGraph教程.assets/image-20240921142940641.png)

### Lession 1 : Motivation

> [PPT链接](https://files.cdn.thinkific.com/file_uploads/967498/attachments/ecd/3cc/6d3/LangChain_Academy_-_Introduction_to_LangGraph_-_Motivation.pdf)

![image-20240921143225567](./LangGraph教程.assets/image-20240921143225567.png)

单独的语言模型是相当有限的。例如访问工具、外部环境、多步骤工作流。

![image-20240921143256065](./LangGraph教程.assets/image-20240921143256065.png)

因此，许多大模型应用都需要控制流，前后可能需要多次调用大模型来帮助处理（工具调用、检索等）。

![image-20240921151606852](./LangGraph教程.assets/image-20240921151606852.png)

控制流形成了链（chain）

![image-20240921151614089](./LangGraph教程.assets/image-20240921151614089.png)

因为每次调用都保证了同样的控制流，所以链是可靠的

![image-20240921151624524](./LangGraph教程.assets/image-20240921151624524.png)

但我们想要大模型系统能选择他们自己的控制流。

![image-20240921151633419](./LangGraph教程.assets/image-20240921151633419.png)

Agent ≈ 控制由大模型定义的流。与链不同，给定 LLM对应用程序中的步骤顺序有一定程度的控制，比如：使用 LLM 在两条潜在路径之间布线；使用 LLM 来决定调用众多工具中的哪一个；使用 LLM 来确定生成的答案是否足够或需要更多工作

![image-20240921151642141](./LangGraph教程.assets/image-20240921151642141.png)

固定控制流 vs 大模型定义的控制流

![image-20240921151648360](./LangGraph教程.assets/image-20240921151648360.png)

有许多不同类型的[代理架构](https://blog.langchain.dev/what-is-a-cognitive-architecture/)需要考虑，给定 LLM 具有不同级别的控制。从**路由选择**到**全自动**，控制要求越来越高。一个极端是，路由选择允许 LLM 从一组指定的选项中选择单个步骤；而在另一个极端，一个完全自主的长期运行agent可以完全自由地为给定问题选择它想要的任何步骤序列。

![image-20240921152903202](./LangGraph教程.assets/image-20240921152903202.png)![image-20240921153053564](./LangGraph教程.assets/image-20240921153053564.png)

在实践中，经常需要在控制和可靠性之间进行权衡（更高的智能伴随更低的可信度）。当我们给 LLMs 更多的控制权时，应用程序通常会变得不那么可靠。这可能是由于 LLM 不确定性和/或选择代理使用（或采取）的工具（或步骤）时的错误等因素造成的。

![image-20240921151707725](./LangGraph教程.assets/image-20240921151707725.png)![image-20240921153118038](./LangGraph教程.assets/image-20240921153118038.png)

LangGraph帮助你掰弯可信曲线，在保持智能程度的基础上，尽可能少的损失可信度。

![image-20240921151851716](./LangGraph教程.assets/image-20240921151851716.png)

通常意义上来说，想要可信，就要把控制流一步步拆开。

![image-20240921151900835](./LangGraph教程.assets/image-20240921151900835.png)

想要控制，可以加入LLM来成为一个agent

![image-20240921151907696](./LangGraph教程.assets/image-20240921151907696.png)

现在，使用LangGraph，将**传统的控制流**转换成**图**

![image-20240921151913729](./LangGraph教程.assets/image-20240921151913729.png)

也可以加入不同的模块来增强Agent的能力

![image-20240921154706085](./LangGraph教程.assets/image-20240921154706085.png)

LangGraph的一些重要（支柱性）特征：

- 持续性(Persistence)

> LangGraph 为开发人员提供了许多使用短期或长期（例如，通过数据库）内存[来持久化](https://langchain-ai.github.io/langgraph/how-tos/#persistence)图形状态的选项。

- 流式(Streaming)

> LangGraph 提供了一流的[流式处理](https://langchain-ai.github.io/langgraph/how-tos/#streaming)支持，可以在agent执行过程中向用户（或开发人员）公开状态。LangGraph 支持流式事件（[如进行工具调用](https://langchain-ai.github.io/langgraph/how-tos/stream-updates/)）以及 [LLM 可能发出token](https://langchain-ai.github.io/langgraph/how-tos/streaming-tokens/)。

- 人在回路(Human-in-the-loop)

> 持续性支持与agent的多种不同的[人在回路](https://langchain-ai.github.io/langgraph/how-tos/#human-in-the-loop)模式；例如，可以暂停agent、查看其状态、编辑 IT 状态和批准后续步骤。

- 可控(Controllability)

> LangGraph 通过将应用程序的流程表示为一组节点和边缘，为开发人员提供了高度[的控制权](https://langchain-ai.github.io/langgraph/how-tos/#controllability)。所有节点都可以访问和修改公共状态（内存）。应用程序的控制流可以使用连接节点的 edge 进行设置，无论是确定性地还是通过条件逻辑。



![image-20240921151920653](./LangGraph教程.assets/image-20240921151920653.png)

在后续的四个模块中，会分别学习：路由选择型Agent、记忆、人在回路、定制化

![image-20240921155906753](./LangGraph教程.assets/image-20240921155906753.png)

![image-20240921160013623](./LangGraph教程.assets/image-20240921160013623.png)

![image-20240921160023098](./LangGraph教程.assets/image-20240921160023098.png)

![image-20240921160049360](./LangGraph教程.assets/image-20240921160049360.png)

---

# 好用的轮子

> 基础部分略过，下面只收录我在学习过程中总结的，比较好用的轮子

---

## Basic

### 1. 绑定工具（Module 1-2）

<img src="./LangGraph教程.assets/image-20241118220910768.png" alt="image-20241118220910768"  />

```python
from typing import Annotated
from langgraph.graph.message import add_messages
from typing_extensions import TypedDict
from langchain_core.messages import AnyMessage
from langgraph.graph import StateGraph, START, END
from langchain_core.messages import HumanMessage
from langchain_community.chat_models import ChatZhipuAI
from IPython.display import Image, display

import os
os.environ["ZHIPUAI_API_KEY"] = "YOUR_API_KEY"


class MessagesState(TypedDict):
    messages: Annotated[list[AnyMessage], add_messages]

def multiply(a: int, b: int) -> int:
    return a * b

llm = ChatZhipuAI(model="glm-4-flash")

llm_with_tools = llm.bind_tools([multiply])

def tool_calling_llm(state: MessagesState):
    return {"messages": [llm_with_tools.invoke(state["messages"])]}

# Build graph
builder = StateGraph(MessagesState)
builder.add_node("tool_calling", tool_calling_llm)
builder.add_edge(START, "tool_calling")
builder.add_edge("tool_calling", END)
graph = builder.compile()

# View
display(Image(graph.get_graph().draw_mermaid_png()))

messages = graph.invoke({"messages": HumanMessage(content="Hello!")})
for m in messages['messages']:
    m.pretty_print()

messages = graph.invoke({"messages": HumanMessage(content="Multiply 2 and 3")})
for m in messages['messages']:
    m.pretty_print()

# ================================ Human Message ================================

# Hello!
# ================================== Ai Message =================================

# Hello! How can I assist you today?
# ================================ Human Message ================================

# Multiply 2 and 3
# ================================== Ai Message =================================
# Tool Calls:
#   multiply (call_9216575921612265324)
#  Call ID: call_9216575921612265324
#   Args:
#     a: 2
#     b: 3
```



### 2. 双路由（Module 1-3）

![image-20241118221611746](./LangGraph教程.assets/image-20241118221611746.png)

```python
from langchain_core.messages import HumanMessage
from IPython.display import Image, display
from langgraph.graph import StateGraph, START, END
from langgraph.graph import MessagesState
from langgraph.prebuilt import ToolNode
from langgraph.prebuilt import tools_condition
import os
os.environ["ZHIPUAI_API_KEY"] = "YOUR_API_KEY"

from langchain_community.chat_models import ChatZhipuAI

def multiply(a: int, b: int) -> int:
    """Multiply a and b.

    Args:
        a: first int
        b: second int
    """
    return a * b

llm = ChatZhipuAI(model="glm-4-flash")
llm_with_tools = llm.bind_tools([multiply])

# Node
def tool_calling_llm(state: MessagesState):
    return {"messages": [llm_with_tools.invoke(state["messages"])]}

# Build graph
builder = StateGraph(MessagesState)
builder.add_node("tool_calling_llm", tool_calling_llm)
builder.add_node("tools", ToolNode([multiply]))
builder.add_edge(START, "tool_calling_llm")
builder.add_conditional_edges(
    "tool_calling_llm",
    # 如果assistant最新的消息（结果）是一个工具调用 -> tools_condition 路由到 tools
    # 如果assistant最新的消息（结果）不是一个工具调用 -> tools_condition 路由到 END
    tools_condition,
)
builder.add_edge("tools", END)
graph = builder.compile()

# View
display(Image(graph.get_graph().draw_mermaid_png()))

messages = [HumanMessage(content="Hello,World!")]
messages = graph.invoke({"messages": messages})
for m in messages['messages']:
    m.pretty_print()
# ================================ Human Message =================================

# Hello,World!
# ================================== Ai Message ==================================

# 你好，世界！很高兴见到你，有什么我可以帮助你的吗？


messages = [HumanMessage(content="12×11的结果是多少.")]
messages = graph.invoke({"messages": messages})
for m in messages['messages']:
    m.pretty_print()
# ================================ Human Message =================================

# 12×11的结果是多少.
# ================================== Ai Message ==================================
# Tool Calls:
#   multiply (call_9216689033873274548)
#  Call ID: call_9216689033873274548
#   Args:
#     a: 12
#     b: 11
# ================================= Tool Message =================================
# Name: multiply

# 132
```

### 2.5. 多路由（Module 1-4）

![image-20241118225748562](./LangGraph教程.assets/image-20241118225748562.png)

```python
from langchain_core.messages import HumanMessage, SystemMessage
from IPython.display import Image, display
from langgraph.graph import StateGraph, START, END
from langgraph.graph import MessagesState
from langgraph.prebuilt import ToolNode
from langgraph.prebuilt import tools_condition
import os
os.environ["ZHIPUAI_API_KEY"] = "YOUR_API_KEY"

from langchain_community.chat_models import ChatZhipuAI

def multiply(a: int, b: int) -> int:
    """Multiply a and b.

    Args:
        a: first int
        b: second int
    """
    return a * b

def add(a: int, b: int) -> int:
    """Adds a and b.

    Args:
        a: first int
        b: second int
    """
    return a + b

def divide(a: int, b: int) -> float:
    """Divide a and b.

    Args:
        a: first int
        b: second int
    """
    return a / b

tools = [add, multiply, divide]

llm = ChatZhipuAI(model="glm-4-flash")

# 对于这个 ipynb，我们将并行工具调用设置为 False，因为数学通常是需要顺序完成的，而这次我们有 3 个可以进行数学运算的工具
# 特别需要注意的是，OpenAI 模型默认为并行工具调用以提高效率，详见 https://python.langchain.com/docs/how_to/tool_calling_parallel/
# 尝试一下，看看模型在处理数学方程时会有什么表现！
llm_with_tools = llm.bind_tools(tools, parallel_tool_calls=False)

# System message
sys_msg = SystemMessage(content="你是一位有帮助的助手，负责对一组输入进行算术运算。")

# Node
def assistant(state: MessagesState):
   return {"messages": [llm_with_tools.invoke([sys_msg] + state["messages"])]}

# Node
def tool_calling_llm(state: MessagesState):
    return {"messages": [llm_with_tools.invoke(state["messages"])]}

# Build graph
builder = StateGraph(MessagesState)

builder.add_node("assistant", assistant)
builder.add_node("tools", ToolNode(tools))
builder.add_edge(START, "assistant")
builder.add_conditional_edges(
    "assistant",
    # 如果assistant最新的消息（结果）是一个工具调用 -> tools_condition 路由到 tools
    # 如果assistant最新的消息（结果）不是一个工具调用 -> tools_condition 路由到 END
    tools_condition,
)
builder.add_edge("tools", "assistant")
# builder.add_edge("tools", END)
graph = builder.compile()

# View
display(Image(graph.get_graph().draw_mermaid_png()))

messages = [HumanMessage(content="3+4之后乘以2，再除以5")]
messages = graph.invoke({"messages": messages})
for m in messages['messages']:
    m.pretty_print() 
# ================================ Human Message =================================

# 3+4之后乘以2，再除以5
# ================================== Ai Message =================================
# Tool Calls:
#   multiply (call_9216575852892724959)
#  Call ID: call_9216575852892724959
#   Args:
#     a: 7
#     b: 2
# ================================= Tool Message =================================
# Name: multiply

# 14
# ================================== Ai Message ==================================
# Tool Calls:
#   multiply (call_9216575578014531059)
#  Call ID: call_9216575578014531059
#   Args:
#     a: 14
#     b: 2
# ================================= Tool Message =================================
# Name: multiply

# 28
# ================================== Ai Message ==================================
# Tool Calls:
#   divide (call_9216580113501986310)
#  Call ID: call_9216580113501986310
#   Args:
#     a: 28
#     b: 5
# ================================ Tool Message =================================
# Name: divide

# 5.6
# ================================= Ai Message ==================================

# 根据您的描述，3+4之后乘以2，再除以5的结果是5.6。
```

### 3. Pydantic数据验证（Module 2-1）

- 使用python的`typing`模块中的`TypedDict`类指定键及其对应的值类型，但它们不会在运行时强制执行类型。
- 这意味着你可能会分配无效的值而不会引发错误！
- 例如，我们可以将 `mood` 设置为 `mad`，尽管我们的类型提示指定了 `mood: list[Literal["happy","sad"]]`。

```python
from typing_extensions import TypedDict
from dataclasses import dataclass
from typing import Literal

class TypedDictState(TypedDict):
    name: str
    mood: Literal["happy","sad"]

@dataclass
class DataclassState:
    name: str
    mood: Literal["happy","sad"]

#即使错了也发现不了
dataclass_instance = DataclassState(name="Lance", mood="mad")
```

- [Pydantic](https://docs.pydantic.dev/latest/api/base_model/) 是一个使用 Python 类型注解进行数据验证和设置管理的库。
- 由于它的验证功能，它非常适合 [在 LangGraph 中定义状态模式](https://langchain-ai.github.io/langgraph/how-tos/state-model/)。
- Pydantic 可以执行验证，以检查数据是否在运行时符合指定的类型和约束。

```python
from pydantic import BaseModel, field_validator, ValidationError
# Pydantic 可以执行验证，以检查数据是否在运行时符合指定的类型和约束。
class PydanticState(BaseModel):
    name: str
    mood: str # "happy" or "sad" 

    @field_validator('mood')
    @classmethod
    # 这里的执行顺序是：
    # @classmethod 装饰器首先应用，将 validate_mood 方法转换为一个类方法。
    # 然后 @field_validator('mood') 装饰器应用在已经转换为类方法的方法上。
    # 这种组合允许 validate_mood 方法既可以通过类直接调用，也可以在字段验证时自动触发。具体来说，当 Pydantic 模型中的 mood 字段被赋值时，validate_mood 方法会被自动调用以进行验证。
    def validate_mood(cls, value):
        # Ensure the mood is either "happy" or "sad"
        if value not in ["happy", "sad"]:
            raise ValueError("Each mood must be either 'happy' or 'sad'")
        return value

try:
    state = PydanticState(name="John Doe", mood="mad")
except ValidationError as e:
    print("Validation Error:", e)

# Validation Error: 1 validation error for PydanticState
# mood
#   Value error, Each mood must be either 'happy' or 'sad' [type=value_error, input_value='mad', input_type=str]
#     For further information visit https://errors.pydantic.dev/2.9/v/value_error
```

Graph

![image-20241119101641926](./LangGraph教程.assets/image-20241119101641926.png)

```python
import random
from IPython.display import Image, display
from langgraph.graph import StateGraph, START, END
from pydantic import BaseModel, field_validator


class PydanticState(BaseModel):
    name: str
    mood: str # "happy" or "sad" 

    @field_validator('mood')
    @classmethod
    # 这里的执行顺序是：
    # @classmethod 装饰器首先应用，将 validate_mood 方法转换为一个类方法。
    # 然后 @field_validator('mood') 装饰器应用在已经转换为类方法的方法上。
    # 这种组合允许 validate_mood 方法既可以通过类直接调用，也可以在字段验证时自动触发。具体来说，当 Pydantic 模型中的 mood 字段被赋值时，validate_mood 方法会被自动调用以进行验证。
    def validate_mood(cls, value):
        # Ensure the mood is either "happy" or "sad"
        if value not in ["happy", "sad"]:
            raise ValueError("Each mood must be either 'happy' or 'sad'")
        return value

def node_1(state):
    print("---Node 1---")
    # state['name'] -> state.name
    # 对于 `dataclass` state ，我们使用 `state.name` 而不是 `TypedDict` 的 `state["name"]`
    return {"name": state.name + " is ... "}

def node_2(state):
    print("---Node 2---")
    return {"mood": "happy"}

def node_3(state):
    print("---Node 3---")
    return {"mood": "sad"}

def decide_mood(state) -> Literal["node_2", "node_3"]:
        
    # Here, let's just do a 50 / 50 split between nodes 2, 3
    if random.random() < 0.5:

        # 50% of the time, we return Node 2
        return "node_2"
    
    # 50% of the time, we return Node 3
    return "node_3"

# Build graph
builder = StateGraph(PydanticState)
builder.add_node("node_1", node_1)
builder.add_node("node_2", node_2)
builder.add_node("node_3", node_3)

# Logic
builder.add_edge(START, "node_1")
builder.add_conditional_edges("node_1", decide_mood)
builder.add_edge("node_2", END)
builder.add_edge("node_3", END)

# Add
graph = builder.compile()

# View
display(Image(graph.get_graph().draw_mermaid_png()))

graph.invoke(PydanticState(name="Lance",mood="sad"))
# ---Node 1---
# ---Node 3---

# {'name': 'Lance is ... ', 'mood': 'sad'}
```

### 4. 过滤之前的消息（前面记录全部删除，只保留最后两条消息）（Module 2-4）

```python
from langchain_core.messages import AIMessage, HumanMessage,RemoveMessage
from IPython.display import Image, display
from langgraph.graph import MessagesState
from langgraph.graph import StateGraph, START, END
from langchain_community.chat_models import ChatZhipuAI
from pprint import pprint
import os
os.environ["ZHIPUAI_API_KEY"] = "YOUR_API_KEY"

llm = ChatZhipuAI(model="glm-4-flash")

messages = [AIMessage("你好.", name="Bot", id="1")]
messages.append(HumanMessage("你好.", name="Linky", id="2"))
messages.append(AIMessage(f"你好，我是你的智能助手Linky。", name="Bot"))
messages.append(HumanMessage(f"你好，我想知道北欧有哪些旅游国家？", name="Linky"))


def filter_messages(state: MessagesState):
    # 调用RemoveMessage，保留最近两条消息
    delete_messages = [RemoveMessage(id=m.id) for m in state["messages"][:-2]]
    return {"messages": delete_messages}

# Node
def chat_model_node(state: MessagesState):
    return {"messages": llm.invoke(state["messages"])}

# Build graph
builder = StateGraph(MessagesState)
builder.add_node("filter", filter_messages)
builder.add_node("chat_model", chat_model_node)
builder.add_edge(START, "filter")
builder.add_edge("filter", "chat_model")
builder.add_edge("chat_model", END)
graph = builder.compile()

# View
display(Image(graph.get_graph().draw_mermaid_png()))

output = graph.invoke({'messages': messages})
for m in output['messages']:
    m.pretty_print()
#================================== Ai Message ==================================
# Name: Bot

# 你好，我是你的智能助手Linky。
# ================================ Human Message =================================
# Name: Linky

# 你好，我想知道北欧有哪些旅游国家？
# ================================== Ai Message ==================================

# 北欧是一个由五个国家组成的地区，通常包括以下这些国家：

# 1. 瑞典（Sweden）
# 2. 挪威（Norway）
# 3. 丹麦（Denmark）
# 4. 芬兰（Finland）
# 5. 冰岛（Iceland）

# 这些国家因其美丽的自然风光、丰富的文化遗产和独特的生活方式而吸引着世界各地的游客。以下是对每个国家的简要介绍：

# - **瑞典**：以其森林、湖泊和著名的哥特堡等历史城市而闻名。
# - **挪威**：拥有壮丽的峡湾和冰川，以及奥斯陆等历史悠久的城市。
# - **丹麦**：以其童话般的城堡、历史悠久的教堂和现代设计的城市而著称。
# - **芬兰**：以圣诞老人的故乡闻名，还有美丽的湖泊和芬兰森林。
# - **冰岛**：以其活跃的火山、瀑布、热泉和北极光而闻名。

# 每个国家都有独特的旅游景点和体验，值得游客深入探索。
```

### 4.5. 过滤之前的消息（前面记录保持不变，只使用最后一条喂给LLM）（Module 2-4）

- 下面的例子有一个bug，只使用最后一条的话，之前的记录LLM是不知道的，所以这种技巧只适合单轮对话，只是保存过去的聊天记录

```python
from langchain_core.messages import AIMessage, HumanMessage,RemoveMessage
from IPython.display import Image, display
from langgraph.graph import MessagesState
from langgraph.graph import StateGraph, START, END
from langchain_community.chat_models import ChatZhipuAI
from pprint import pprint
import os
os.environ["ZHIPUAI_API_KEY"] = "YOUR_API_KEY"

llm = ChatZhipuAI(model="glm-4-flash")

messages = [AIMessage("你好.", name="Bot", id="1")]
messages.append(HumanMessage("你好.", name="Linky", id="2"))
messages.append(AIMessage(f"你好，我是你的智能助手Linky。", name="Bot"))
messages.append(HumanMessage(f"你好，我想知道北欧有哪些旅游国家？", name="Linky"))


# Node
def chat_model_node(state: MessagesState):
    return {"messages": [llm.invoke(state["messages"][-1:])]}

# Build graph
builder = StateGraph(MessagesState)
builder.add_node("chat_model", chat_model_node)
builder.add_edge(START, "chat_model")
builder.add_edge("chat_model", END)
graph = builder.compile()

# View
display(Image(graph.get_graph().draw_mermaid_png()))


output = graph.invoke({'messages': messages})
for m in output['messages']:
    m.pretty_print()
# ================================== Ai Message ==================================
# Name: Bot

# 你好.
# ================================ Human Message =================================
# Name: Linky

# 你好.
# ================================== Ai Message ==================================
# Name: Bot

# 你好，我是你的智能助手Linky。
# ================================ Human Message =================================
# Name: Linky

# 你好，我想知道北欧有哪些旅游国家？
# ================================== Ai Message ==================================

# 你好！北欧是一个地理和文化上较为独特的地区，主要包括以下五个国家：

# 1. **挪威** - 以壮丽的峡湾和北极光而闻名。
# 2. **瑞典** - 一个拥有许多森林、湖泊和岛屿的国家。
# 3. **芬兰** - 以其冬季运动、圣诞老人村和美丽的自然风光著称。
# 4. **丹麦** - 以其童话故事、安徒生和哥本哈根的美景而知名。
# 5. **冰岛** - 一个充满火山、温泉和地热能的岛国。

# 这些国家都各自拥有独特的文化和自然景观，是旅游爱好者不可错过的目的地。
```

```python
# 获取输出结果，在后面添加一句，但是每次只回答最后一个问题，前面的记录保持不变
messages.append(output['messages'][-1])
messages.append(HumanMessage(f"这些国家中哪一个旅游开销最小", name="Linky"))

output = graph.invoke({'messages': messages})
for m in output['messages']:
    m.pretty_print()
# ================================== Ai Message =================================
# Name: Bot

# 你好.
# ================================ Human Message ================================
# Name: Linky

# 你好.
# ================================== Ai Message =================================
# Name: Bot

# 你好，我是你的智能助手Linky。
# ================================ Human Message ================================
# Name: Linky

# 你好，我想知道北欧有哪些旅游国家？
# ================================== Ai Message =================================

# 你好！北欧是一个地理和文化上较为独特的地区，主要包括以下五个国家：

# 1. **挪威** - 以壮丽的峡湾和北极光而闻名。
# 2. **瑞典** - 一个拥有许多森林、湖泊和岛屿的国家。
# 3. **芬兰** - 以其冬季运动、圣诞老人村和美丽的自然风光著称。
# 4. **丹麦** - 以其童话故事、安徒生和哥本哈根的美景而知名。
# 5. **冰岛** - 一个充满火山、温泉和地热能的岛国。

# 这些国家都各自拥有独特的文化和自然景观，是旅游爱好者不可错过的目的地。
# ================================ Human Message ================================
# Name: Linky

# 这些国家中哪一个旅游开销最小
# ================================== Ai Message =================================

# 旅游开销的大小受多种因素影响，包括国家或地区的物价水平、住宿、交通、餐饮等。以下是一些通常被认为旅游开销较小的国家：

# 1. 亚洲国家：如泰国、越南、柬埔寨、印度尼西亚、菲律宾等，这些国家的物价普遍较低，适合预算旅行者。

# 2. 南美洲国家：如秘鲁、玻利维亚、哥伦比亚、厄瓜多尔等，这些地区也有不错的旅游资源和相对较低的物价。

# 3. 非洲国家：如摩洛哥、埃及、南非、坦桑尼亚等，虽然一些地区可能存在安全风险，但相对其他热门旅游目的地，开销可能较低。

# 4. 俄罗斯和东欧国家：如俄罗斯、波兰、捷克、匈牙利等，这些国家的生活成本相对较低，旅游开销也相对较小。

# 需要注意的是，这些只是一些大致的指南，具体开销还需根据个人旅行习惯和具体行程来定。建议在规划旅行前，对目的地进行详细的研究和预算规划。
```



### 5. 总结对话（Module 2-5）

- Session内有效，即只总结当前Graph中的对话消息

![image-20241119130503196](./LangGraph教程.assets/image-20241119130503196.png)

```python
from langchain_core.messages import SystemMessage,AIMessage, HumanMessage, RemoveMessage
from IPython.display import Image, display
from langgraph.graph import MessagesState
from langgraph.checkpoint.memory import MemorySaver
from langgraph.graph import StateGraph, START, END
from langchain_community.chat_models import ChatZhipuAI
from pprint import pprint
import os
os.environ["ZHIPUAI_API_KEY"] = "YOUR_API_KEY"

class State(MessagesState):
    summary: str

llm = ChatZhipuAI(model="glm-4-flash")

def call_model(state: State):
    # 获取摘要（如果存在）
    summary = state.get("summary", "")
    # 如果存在摘要，则添加它
    if summary:
        # 将摘要添加到系统消息中
        system_message = f"Summary of conversation earlier: {summary}"
        # 将摘要附加到任何新消息中
        messages = [SystemMessage(content=system_message)] + state["messages"]
    else:
        messages = state["messages"]
    
    response = llm.invoke(messages)
    return {"messages": response}

def summarize_conversation(state: State):
    # 首先，获取任何现有的摘要
    summary = state.get("summary", "")
    # 然后，创建摘要的prompt
    if summary:
        summary_message = (
            f"到目前为止的对话摘要如下：{summary}\n\n"
            "请根据上述新消息扩展摘要："
        )
    else:
        summary_message = "创建上述对话的摘要："
    # 将提示添加到我们的历史记录中
    messages = state["messages"] + [HumanMessage(content=summary_message)]
    response = llm.invoke(messages)
    
    # 删除除了最后两个消息之外的所有消息
    delete_messages = [RemoveMessage(id=m.id) for m in state["messages"][:-2]]
    return {"summary": response.content, "messages": delete_messages}

def should_continue(state: State):
    """返回要执行的下一个节点。"""
    messages = state["messages"]
    
    # 如果有超过6条消息，则总结对话
    if len(messages) > 6:
        return "summarize_conversation"
    # 否则，结束对话
    return END


# 定义一个新的图
workflow = StateGraph(State)
workflow.add_node("conversation", call_model)
workflow.add_node(summarize_conversation)

# 设置入口点为对话
workflow.add_edge(START, "conversation")
workflow.add_conditional_edges("conversation", should_continue)
workflow.add_edge("summarize_conversation", END)

# 编译
memory = MemorySaver()
graph = workflow.compile(checkpointer=memory)
display(Image(graph.get_graph().draw_mermaid_png()))

# ===================================================================
# 创建一个线程
config = {"configurable": {"thread_id": "1"}}

# 开始对话
input_message = HumanMessage(content="你好，我是牛可可")
output = graph.invoke({"messages": [input_message]}, config) 
for m in output['messages'][-1:]:
    m.pretty_print()

input_message = HumanMessage(content="我的名字叫什么？")
output = graph.invoke({"messages": [input_message]}, config) 
for m in output['messages'][-1:]:
    m.pretty_print()

input_message = HumanMessage(content="我喜欢看英雄联盟比赛!")
output = graph.invoke({"messages": [input_message]}, config) 
for m in output['messages'][-1:]:
    m.pretty_print()

input_message = HumanMessage(content="我喜欢faker,他是薪资最高的LOL选手吗？")
output = graph.invoke({"messages": [input_message]}, config) 
for m in output['messages'][-1:]:
    m.pretty_print()


# ================================== Ai Message ==================================

# 你好，牛可可！很高兴认识你。有什么可以帮助你的吗？
# ================================== Ai Message ==================================

# 你的名字是牛可可。很高兴和你交流！如果你有任何问题或者需要帮助，请随时告诉我。
# ================================== Ai Message ==================================

# 英雄联盟（League of Legends）是一款非常受欢迎的多人在线战斗竞技场（MOBA）游戏，拥有庞大的玩家基础和丰富的电竞赛事。你喜欢看比赛很酷，因为英雄联盟的比赛充满策略、技巧和团队合作，同时也非常精彩刺激。

# 如果你对比赛有什么特别的兴趣，比如喜欢某个队伍、选手或者特定的游戏模式，不妨分享给我，我们可以一起讨论。另外，如果你想了解更多关于比赛的信息，比如最新的赛事日程、选手资料或者游戏技巧，我也可以提供帮助。
# ================================== Ai Message ==================================

# Faker，本名李相赫（Lee Sang-hyeok），是韩国的一名著名英雄联盟职业选手，被广泛认为是历史上最伟大的LOL选手之一。他以在韩国SK Telecom T1（现称为T1）队伍中的表现而闻名。

# 关于Faker的薪资，他是职业电竞界的顶尖选手，因此在收入上也是数一数二的。然而，是否是他薪资最高的选手可能不完全确定，因为电竞选手的薪资往往受到多种因素的影响，包括他们所在的队伍、个人品牌、赞助合同等。

# 在电竞领域，一些顶尖选手，尤其是那些在社交媒体上有大量粉丝和影响力的选手，他们的薪资可能会非常高。因此，虽然Faker的薪资确实很高，但他是否是薪资最高的LOL选手，可能需要查阅最新的资料和合同细节来确定。不过可以肯定的是，他是电子竞技界收入相当可观的选手之一。

''' 上面一共有4×2=8条（>6）消息，所以应该总结对话'''
graph.get_state(config).values.get("summary","")
# '摘要：\n- 用户自称为牛可可，表达了对英雄联盟比赛的喜爱，特别是对著名选手Faker的崇拜。\n- 讨论了Faker作为顶尖选手的收入情况，虽然他可能是薪资最高的LOL选手之一，但具体是否最高需要查阅最新资料。'

```



## Memory

### 1. 保存在本地SQLite（Module 2-6）

- 关闭Session仍然有效，即重新启动代码仍然可以从磁盘上的Sqlite数据库中加载总结好的数据

![image-20241119131913958](./LangGraph教程.assets/image-20241119131913958.png)

```python
'''下面语句用于测试，清空数据
# # 连接到数据库
# conn = sqlite3.connect('state_db/example.db')
# cursor = conn.cursor()

# # 编写并执行 DELETE 语句
# cursor.execute("DELETE FROM writes WHERE thread_id = 1")

# # 提交事务
# conn.commit()

# # 关闭连接
# conn.close()
'''

# 如果文件不存在，则拉取文件并连接到本地数据库
# !mkdir -p state_db && [ ! -f state_db/example.db ] && wget -P state_db https://github.com/langchain-ai/langchain-academy/raw/main/module-2/state_db/example.db
import sqlite3
from langgraph.checkpoint.sqlite import SqliteSaver
from langchain_core.messages import SystemMessage, HumanMessage, RemoveMessage
from IPython.display import Image, display
from langgraph.graph import MessagesState
from langgraph.graph import StateGraph, START, END
from langchain_community.chat_models import ChatZhipuAI
import os
os.environ["ZHIPUAI_API_KEY"] = "YOUR_API_KEY"

db_path = "./state_db/example.db"
conn = sqlite3.connect(db_path, check_same_thread=False)

# 这是我们的checkpointer 
memory = SqliteSaver(conn)

llm = ChatZhipuAI(model="glm-4-flash")

class State(MessagesState):
    summary: str
# 定义调用模型的逻辑
def call_model(state: State):
    # 获取摘要（如果存在）
    summary = state.get("summary", "")
    # 如果有摘要，则添加它
    if summary:
        # 将摘要添加到系统消息中
        system_message = f"之前的对话摘要：{summary}"
        # 将摘要附加到任何更新的消息中
        messages = [SystemMessage(content=system_message)] + state["messages"]
    else:
        messages = state["messages"]
    response = llm.invoke(messages)
    return {"messages": response}

def summarize_conversation(state: State):
    # 首先获取现有的摘要
    summary = state.get("summary", "")
    # 创建我们的摘要prompt
    if summary:
        summary_message = (
            f"到目前为止的对话摘要如下：{summary}\n\n"
            "请根据上述新消息扩展摘要："
        )
    else:
        summary_message = "创建上述对话的摘要："

    # 将提示添加到我们的历史记录中
    messages = state["messages"] + [HumanMessage(content=summary_message)]
    response = llm.invoke(messages)
    
    # 删除除了最新的两条消息之外的所有消息
    delete_messages = [RemoveMessage(id=m.id) for m in state["messages"][:-2]]
    return {"summary": response.content, "messages": delete_messages}


# 确定是否结束或总结对话
def should_continue(state: State):
    """返回要执行的下一个节点。"""
    messages = state["messages"]
    # 如果消息数量超过六条，那么我们将总结对话
    if len(messages) > 6:
        return "summarize_conversation"
    # 否则我们可以直接结束
    return END

# 定义一个新的图
workflow = StateGraph(State)
workflow.add_node("conversation", call_model)
workflow.add_node(summarize_conversation)

# 设置入口点为对话
workflow.add_edge(START, "conversation")
workflow.add_conditional_edges("conversation", should_continue)
workflow.add_edge("summarize_conversation", END)

# 编译
graph = workflow.compile(checkpointer=memory)
display(Image(graph.get_graph().draw_mermaid_png()))
```

```python
# 创建一个线程
config = {"configurable": {"thread_id": "1"}}

# 开始对话
input_message = HumanMessage(content="你好，我是牛可可")
output = graph.invoke({"messages": [input_message]}, config) 
for m in output['messages'][-2:]:
    m.pretty_print()

input_message = HumanMessage(content="我的名字叫什么？")
output = graph.invoke({"messages": [input_message]}, config) 
for m in output['messages'][-2:]:
    m.pretty_print()

input_message = HumanMessage(content="我喜欢看英雄联盟比赛!")
output = graph.invoke({"messages": [input_message]}, config) 
for m in output['messages'][-2:]:
    m.pretty_print()
# ================================  Human Message  =================================

# 你好，我是牛可可
# ==================================  Ai Message  ==================================

# 你好，牛可可！很高兴认识你。有什么可以帮助你的吗？
# ================================  Human Message  =================================

# 我的名字叫什么？
# ==================================  Ai Message  ==================================

# 你的名字是牛可可。很高兴在这里和你交流！有什么问题或者话题你想讨论吗？
# ================================  Human Message  =================================

# 我喜欢看英雄联盟比赛!
# ==================================  Ai Message  ==================================

# 英雄联盟（League of Legends）确实是一款非常受欢迎的多人在线战斗竞技游戏，有很多忠实的玩家和粉丝。喜欢看英雄联盟比赛是一件很酷的事情，不仅可以享受到紧张刺激的比赛氛围，还能学习到很多战术和技巧。

# 如果你喜欢看比赛，你可能对以下几个话题感兴趣：
# - 最喜欢的战队或选手
# - 近期的比赛亮点
# - 比赛分析或评论
# - 游戏更新和平衡性改动

# 有没有特定的战队、选手或者比赛你特别喜欢的？或者有什么问题想要讨论的？

'''关闭session之后，重新运行graph，直接运行下面语句，可以获取已经被保存在本地的聊天记录'''
config = {"configurable": {"thread_id": "1"}}
graph_state = graph.get_state(config)
graph_state
# StateSnapshot(values={'messages': [HumanMessage(content='你好，我是牛可可', additional_kwargs={}, response_metadata={}, id='f431dd3d-67f5-41d9-99a2-f4928d2c8a38'), AIMessage(content='你好，牛可可！很高兴认识你。有什么可以帮助你的吗？', additional_kwargs={}, response_metadata={'token_usage': {'completion_tokens': 16, 'prompt_tokens': 10, 'total_tokens': 26}, 'model_name': 'glm-4-flash', 'finish_reason': 'stop'}, id='run-fc439f17-2de4-4e6f-a6e7-1f522244f337-0'), HumanMessage(content='我的名字叫什么？', additional_kwargs={}, response_metadata={}, id='222296dc-6569-413e-a6ba-06b86e6350f9'), AIMessage(content='你的名字是牛可可。很高兴在这里和你交流！有什么问题或者话题你想讨论吗？', additional_kwargs={}, response_metadata={'token_usage': {'completion_tokens': 21, 'prompt_tokens': 33, 'total_tokens': 54}, 'model_name': 'glm-4-flash', 'finish_reason': 'stop'}, id='run-7817b945-452a-4504-897e-4a6ca2da27f0-0'), HumanMessage(content='我喜欢看英雄联盟比赛!', additional_kwargs={}, response_metadata={}, id='c3e0fa81-d0d2-4d01-a189-e9438e435518'), AIMessage(content='英雄联盟（League of Legends）确实是一款非常受欢迎的多人在线战斗竞技游戏，有很多忠实的玩家和粉丝。喜欢看英雄联盟比赛是一件很酷的事情，不仅可以享受到紧张刺激的比赛氛围，还能学习到很多战术和技巧。\n\n如果你喜欢看比赛，你可能对以下几个话题感兴趣：\n- 最喜欢的战队或选手\n- 近期的比赛亮点\n- 比赛分析或评论\n- 游戏更新和平衡性改动\n\n有没有特定的战队、选手或者比赛你特别喜欢的？或者有什么问题想要讨论的？', additional_kwargs={}, response_metadata={'token_usage': {'completion_tokens': 111, 'prompt_tokens': 61, 'total_tokens': 172}, 'model_name': 'glm-4-flash', 'finish_reason': 'stop'}, id='run-83099bdb-5920-487d-a954-a419b57d8819-0')]}, next=(), config={'configurable': {'thread_id': '1', 'checkpoint_ns': '', 'checkpoint_id': '1efa6360-2588-6f32-8007-69c218ef2535'}}, metadata={'source': 'loop', 'writes': {'conversation': {'messages': AIMessage(content='英雄联盟（League of Legends）确实是一款非常受欢迎的多人在线战斗竞技游戏，有很多忠实的玩家和粉丝。喜欢看英雄联盟比赛是一件很酷的事情，不仅可以享受到紧张刺激的比赛氛围，还能学习到很多战术和技巧。\n\n如果你喜欢看比赛，你可能对以下几个话题感兴趣：\n- 最喜欢的战队或选手\n- 近期的比赛亮点\n- 比赛分析或评论\n- 游戏更新和平衡性改动\n\n有没有特定的战队、选手或者比赛你特别喜欢的？或者有什么问题想要讨论的？', additional_kwargs={}, response_metadata={'token_usage': {'completion_tokens': 111, 'prompt_tokens': 61, 'total_tokens': 172}, 'model_name': 'glm-4-flash', 'finish_reason': 'stop'}, id='run-83099bdb-5920-487d-a954-a419b57d8819-0')}}, 'thread_id': '1', 'step': 7, 'parents': {}}, created_at='2024-11-19T05:20:36.957777+00:00', parent_config={'configurable': {'thread_id': '1', 'checkpoint_ns': '', 'checkpoint_id': '1efa635f-fb83-6305-8006-6d0c73f5b82f'}}, tasks=())
```



### 2. 记忆存储（Module 5-1）

我们希望聊天机器人具有两种类型的记忆：

1. `短期（在对话内）记忆（within-thread）`：聊天机器人可以持久保存对话历史，并允许在聊天会话中中断。
2. `长期（跨对话）记忆（cross-thread）`：聊天机器人可以在所有聊天会话中记住关于特定用户的信息。

![image-20241119214618297](./LangGraph教程.assets/image-20241119214618297.png)

```python
from langgraph.store.memory import InMemoryStore
from langchain_community.chat_models import ChatZhipuAI
from IPython.display import Image, display
from langgraph.store.memory import InMemoryStore
from langgraph.checkpoint.memory import MemorySaver
from langgraph.graph import StateGraph, MessagesState, START, END
from langgraph.store.base import BaseStore
from langchain_core.messages import HumanMessage, SystemMessage
from langchain_core.runnables.config import RunnableConfig
import os
os.environ["ZHIPUAI_API_KEY"] = "YOUR_API_KEY"


# 聊天机器人指令
MODEL_SYSTEM_MESSAGE = """你是一个具有记忆功能的助手，可以提供关于用户的信息。
如果你有这个用户的记忆，请用它来个性化你的回答。
这是记忆（可能为空）： 
 {memory}"""

# 从聊天历史和任何现有的记忆中创建新的记忆
CREATE_MEMORY_INSTRUCTION = """"你正在收集用户信息以个性化你的回答。

当前用户信息：
{memory}

要求：
1. 仔细审查下面的聊天历史
2. 识别用户的新信息，例如：
   - 个人详情（姓名、地点）
   - 偏好（喜欢、不喜欢）
   - 兴趣和爱好
   - 过去的经历
   - 目标或未来的计划
3. 将任何新信息与现有记忆合并
4. 将记忆格式化为清晰的 bulleted 列表
5. 如果新信息与现有记忆冲突，保留最新版本

记住：只包括用户直接陈述的事实信息。不要做假设或推断。

根据下面的聊天历史，请更新用户信息：
"""

llm = ChatZhipuAI(model="glm-4-plus")

def call_model(state: MessagesState, config: RunnableConfig, store: BaseStore):
    """从存储中加载记忆，并用它来个性化聊天机器人的回答。"""
    
    # 从配置中获取用户 ID
    user_id = config["configurable"]["user_id"]

    # 从存储中检索记忆
    namespace = ("memory", user_id)
    key = "user_memory"
    existing_memory = store.get(namespace, key)

    # 提取记忆
    if existing_memory:
        # 值是一个带有记忆键的字典
        existing_memory_content = existing_memory.value.get('memory')
    else:
        existing_memory_content = "没有相关记忆."

    # 在系统提示中格式化记忆
    system_msg = MODEL_SYSTEM_MESSAGE.format(memory=existing_memory_content)
    
    # 使用记忆和聊天历史回答
    response = llm.invoke([SystemMessage(content=system_msg)]+state["messages"])

    return {"messages": response}

def write_memory(state: MessagesState, config: RunnableConfig, store: BaseStore):
    """反思聊天历史并保存记忆到存储中。"""
    
    # 从配置中获取用户 ID
    user_id = config["configurable"]["user_id"]

    # 从存储中检索现有记忆
    namespace = ("memory", user_id)
    existing_memory = store.get(namespace, "user_memory")
        
    # 提取记忆
    if existing_memory:
        existing_memory_content = existing_memory.value.get('memory')
    else:
        existing_memory_content = "没有相关记忆."

    # 在系统提示中格式化记忆
    system_msg = CREATE_MEMORY_INSTRUCTION.format(memory=existing_memory_content)
    new_memory = llm.invoke([SystemMessage(content=system_msg)]+state['messages'])

    # 覆盖存储中的现有记忆 
    key = "user_memory"

    # 将值作为带有记忆键的字典写入
    store.put(namespace, key, {"memory": new_memory.content})

# 定义图
builder = StateGraph(MessagesState)
builder.add_node("call_model", call_model)
builder.add_node("write_memory", write_memory)
builder.add_edge(START, "call_model")
builder.add_edge("call_model", "write_memory")
builder.add_edge("write_memory", END)

# 用于长期（跨线程）记忆的存储
across_thread_memory = InMemoryStore()

# 用于短期（在线程内）记忆的检查点
within_thread_memory = MemorySaver()

# 使用检查点和存储编译图
graph = builder.compile(checkpointer=within_thread_memory, store=across_thread_memory)

# 可视化
display(Image(graph.get_graph(xray=1).draw_mermaid_png()))
```

```python
# 我们为短期（在对话内）记忆提供一个线程ID
# 我们为长期（跨对话）记忆提供一个用户ID

config = {"configurable": {"thread_id": "1", "user_id": "1"}}

# User input 
input_messages = [HumanMessage(content="你好，我的名字是牛可可")]

# Run the graph
for chunk in graph.stream({"messages": input_messages}, config, stream_mode="values"):
    chunk["messages"][-1].pretty_print()

# ================================ Human Message =================================

# 你好，我的名字是牛可可
# ================================== Ai Message ==================================

# 你好，牛可可！很高兴认识你。如果你有任何问题或者需要帮助，随时告诉我，我会尽力协助你。希望我们能愉快地交流！🌟
```

```python
# 用户输入
input_messages = [HumanMessage(content="我喜欢沿着黄浦江边骑行")]

# 运行图
for chunk in graph.stream({"messages": input_messages}, config, stream_mode="values"):
    chunk["messages"][-1].pretty_print()

# ================================ Human Message =================================

# 我喜欢沿着黄浦江边骑行
# ================================== Ai Message ==================================

# 那真是太棒了！沿着黄浦江边骑行不仅风景优美，还能感受到上海这座城市的独特魅力。你可以一边骑行一边欣赏对岸的陆家嘴天际线，或者是感受江边的微风，非常惬意。

# 如果你有兴趣，可以分享一些你骑行时的有趣经历或者最喜欢的一段路线。另外，如果你需要推荐一些骑行装备或者想要了解更多的骑行路线，我也很乐意为你提供信息哦！🚴‍♀️🌊
```

```python
# 保存记忆的命名空间
user_id = "1"
namespace = ("memory", user_id)
existing_memory = across_thread_memory.get(namespace, "user_memory")

# existing_memory.dict()
# {'value': {'memory': '**更新后的用户信息：**\n\n- **个人详情**\n  - 姓名：牛可可\n\n- **兴趣和爱好**\n  - 骑行\n  - 沿着黄浦江边骑行\n\n目前其他类别（偏好、过去的经历、目标或未来的计划）仍然没有相关记忆。如果有更多聊天历史，请提供以便进一步更新用户信息。'},
#  'key': 'user_memory',
#  'namespace': ['memory', '1'],
#  'created_at': '2024-11-19T13:41:21.284399+00:00',
#  'updated_at': '2024-11-19T13:41:28.865615+00:00'}

print(existing_memory.dict()['value']['memory'])
# **更新后的用户信息：**

# - **个人详情**
#   - 姓名：牛可可

# - **兴趣和爱好**
#   - 骑行
#   - 沿着黄浦江边骑行

# 目前其他类别（偏好、过去的经历、目标或未来的计划）仍然没有相关记忆。如果有更多聊天历史，请提供以便进一步更新用户信息。
```

```python
# 我们同时为跨线程记忆提供一个用户ID以及一个新的线程ID
config = {"configurable": {"thread_id": "2", "user_id": "1"}}

# 用户输入
input_messages = [HumanMessage(content="嗨！你推荐我去哪里骑行？")]

# 运行图
for chunk in graph.stream({"messages": input_messages}, config, stream_mode="values"):
    chunk["messages"][-1].pretty_print()
    
# ================================ Human Message =================================

# 嗨！你推荐我去哪里骑行？
# ================================== Ai Message ==================================

# 嗨，牛可可！既然你喜欢沿着黄浦江边骑行，我有一些推荐的地方，希望能让你的骑行体验更加丰富和愉快：

# 1. **黄浦江滨江大道**：
#    - 这是一条非常经典的骑行路线，沿途可以欣赏到上海的地标建筑，如东方明珠、上海中心大厦等。路况良好，适合悠闲骑行。

# 2. **徐汇滨江绿地**：
#    - 这里不仅有宽阔的骑行道，还有艺术氛围浓厚的龙美术馆和余德耀美术馆，骑行途中可以顺便参观一下。

# 3. **浦东滨江森林公园**：
#    - 如果你喜欢自然风光，这里是个不错的选择。公园内有专门的骑行道，周围绿树成荫，空气清新。
```

```python
# 用户输入 
input_messages = [HumanMessage(content="太好了，附近有推荐的咖啡店吗？我喜欢在骑行之后来一杯卡布奇诺。")]

# 运行图
for chunk in graph.stream({"messages": input_messages}, config, stream_mode="values"):
    chunk["messages"][-1].pretty_print()

# ================================ Human Message =================================

# 太好了，附近有推荐的咖啡店吗？我喜欢在骑行之后来一杯卡布奇诺。
# ================================== Ai Message ==================================

# 当然有！根据你之前提到的骑行路线，以下是一些附近的咖啡店推荐，希望你在骑行后能享受一杯美味的卡布奇诺：

# 1. **星巴克（东方明珠店）**：
#    - 地址：上海市浦东新区世纪大道1号东方明珠塔内。
#    - 特色：位于地标建筑内，视野绝佳，适合休息和拍照。

# 2. **Seesaw Coffee（徐汇滨江店）**：
#    - 地址：上海市徐汇区龙腾大道3398号。
#    - 特色：高品质的手冲咖啡和舒适的环境，非常适合骑行后放松。

# 3. **Costa Coffee（浦东滨江森林公园店）**：
#    - 地址：上海市浦东新区高桥镇凌桥路1088号。
#    - 特色：靠近自然公园，环境清新，适合骑行后的小憩。

# 这些咖啡店都离你提到的骑行路线不远，非常适合骑行后去享受一杯温暖的卡布奇诺。希望你能在这些地方找到心仪的休息场所，放松身心！🌟🍵🚴‍♀️
```



## Agent

### 1. 中断 + tool use（Module 3-2）

- 在调用工具之前插入中断，让用户判断是否需要调用工具

![image-20241119145724275](./LangGraph教程.assets/image-20241119145724275.png)

```python
from langchain_community.chat_models import ChatZhipuAI
import os
os.environ["ZHIPUAI_API_KEY"] = "YOUR_API_KEY"


def multiply(a: int, b: int) -> int:
    """Multiply a and b.

    Args:
        a: first int
        b: second int
    """
    return a * b

# This will be a tool
def add(a: int, b: int) -> int:
    """Adds a and b.

    Args:
        a: first int
        b: second int
    """
    return a + b

def divide(a: int, b: int) -> float:
    """Adds a and b.

    Args:
        a: first int
        b: second int
    """
    return a / b

tools = [add, multiply, divide]
llm = ChatZhipuAI(model="glm-4-plus")
llm_with_tools = llm.bind_tools(tools)

from IPython.display import Image, display

from langgraph.checkpoint.memory import MemorySaver
from langgraph.graph import MessagesState
from langgraph.graph import START, StateGraph
from langgraph.prebuilt import tools_condition, ToolNode

from langchain_core.messages import AIMessage, HumanMessage, SystemMessage

# 系统消息
sys_msg = SystemMessage(content="你是一个乐于助人的助手，负责对一组输入进行算术运算。")

# 节点定义
def assistant(state: MessagesState):
   return {"messages": [llm_with_tools.invoke([sys_msg] + state["messages"])]}

# 图定义
builder = StateGraph(MessagesState)

# 定义节点：这些节点负责执行工作
builder.add_node("assistant", assistant)
builder.add_node("tools", ToolNode(tools))

# 定义边：这些边决定控制流
builder.add_edge(START, "assistant")
builder.add_conditional_edges(
    "assistant",
    # 如果助手最新的消息（结果）是一个工具调用 -> tools_condition 路由到 tools
    # 如果助手最新的消息（结果）不是一个工具调用 -> tools_condition 路由到 END
    tools_condition,
)
builder.add_edge("tools", "assistant")

memory = MemorySaver()
graph = builder.compile(interrupt_before=["tools"], checkpointer=memory)

# 显示图形
display(Image(graph.get_graph(xray=True).draw_mermaid_png()))

# 输入
initial_input = {"messages": HumanMessage(content="2和3相乘")}

# 线程
thread = {"configurable": {"thread_id": "2"}}

# 运行图直到第一次中断
for event in graph.stream(initial_input, thread, stream_mode="values"):
    event['messages'][-1].pretty_print()

# 获取用户反馈
user_approval = input("你想要调用工具吗？(是/否): ")

# 检查批准
if user_approval == "是":
    
    # 如果批准，继续执行图
    for event in graph.stream(None, thread, stream_mode="values"):
        event['messages'][-1].pretty_print()
        
else:
    print("操作被用户取消。")
# ================================ Human Message =================================

# 2和3相乘
# ================================== Ai Message ==================================
# Tool Calls:
#   multiply (call_9216580182221462360)
#  Call ID: call_9216580182221462360
#   Args:
#     a: 2
#     b: 3
# ================================== Ai Message ==================================
# Tool Calls:
#   multiply (call_9216580182221462360)
#  Call ID: call_9216580182221462360
#   Args:
#     a: 2
#     b: 3
# ================================= Tool Message =================================
# Name: multiply

# 6
# ================================== Ai Message ==================================

# 2和3相乘的结果是6。
```





### 2. 中断 + Human-in-the-loop（Module 3-3）

- 在调用大模型之前中断，让用户判断是否需要修改输入，这个可以放在**预处理数据和调用大模型之间**

![image-20241119150640170](./LangGraph教程.assets/image-20241119150640170.png)

```python
from langchain_community.chat_models import ChatZhipuAI
import os
os.environ["ZHIPUAI_API_KEY"] = "YOUR_API_KEY"


def multiply(a: int, b: int) -> int:
    """Multiply a and b.

    Args:
        a: first int
        b: second int
    """
    return a * b

# This will be a tool
def add(a: int, b: int) -> int:
    """Adds a and b.

    Args:
        a: first int
        b: second int
    """
    return a + b

def divide(a: int, b: int) -> float:
    """Adds a and b.

    Args:
        a: first int
        b: second int
    """
    return a / b

tools = [add, multiply, divide]
llm = ChatZhipuAI(model="glm-4-plus")
llm_with_tools = llm.bind_tools(tools)

from IPython.display import Image, display

from langgraph.checkpoint.memory import MemorySaver
from langgraph.graph import MessagesState
from langgraph.graph import START, StateGraph
from langgraph.prebuilt import tools_condition, ToolNode

from langchain_core.messages import AIMessage, HumanMessage, SystemMessage

# 系统消息
sys_msg = SystemMessage(content="你是一个有帮助的助手，负责对一组输入进行算术运算。")

# 应该被中断的无操作节点
def human_feedback(state: MessagesState):
    pass

# 助手节点
def assistant(state: MessagesState):
   return {"messages": [llm_with_tools.invoke([sys_msg] + state["messages"])]}

# 图
builder = StateGraph(MessagesState)

# 定义节点：这些节点执行工作
builder.add_node("assistant", assistant)
builder.add_node("tools", ToolNode(tools))
builder.add_node("human_feedback", human_feedback)

# 定义边：这些边确定控制流
builder.add_edge(START, "human_feedback")
builder.add_edge("human_feedback", "assistant")
builder.add_conditional_edges(
    "assistant",
    # 如果助手最新的消息（结果）是一个工具调用 -> tools_condition 路由到 tools
    # 如果助手最新的消息（结果）不是一个工具调用 -> tools_condition 路由到 END
    tools_condition,
)
builder.add_edge("tools", "human_feedback")

memory = MemorySaver()
graph = builder.compile(interrupt_before=["human_feedback"], checkpointer=memory)
display(Image(graph.get_graph().draw_mermaid_png()))

# 输入
initial_input = {"messages": "将2和3相乘"}

# 线程
thread = {"configurable": {"thread_id": "4"}}

# 运行图直到第一次中断
for event in graph.stream(initial_input, thread, stream_mode="values"):
    event["messages"][-1].pretty_print()
    
# 获取用户输入
user_input = input("你的修改是: ")

# 我们现在更新状态，就像我们是 human_feedback 节点一样
graph.update_state(thread, {"messages": user_input}, as_node="human_feedback")

# 继续执行图
for event in graph.stream(None, thread, stream_mode="values"):
    event["messages"][-1].pretty_print()

# =============================== Human Message  ================================

# 将2和3相乘
# =============================== Human Message  ================================

# 将27和39相加
# ================================= Ai Message  =================================
# Tool Calls:
#   add (call_9216580147861683457)
#  Call ID: call_9216580147861683457
#   Args:
#     a: 27
#     b: 39
# ================================ Tool Message  ================================
# Name: add

# 66
```

### 3. 并行执行（Module 4-1）

- 搜索引擎 + Wikipedia

![image-20241119171634238](./LangGraph教程.assets/image-20241119171634238.png)

```python
from langchain_core.messages import HumanMessage, SystemMessage
from langchain_community.document_loaders import WikipediaLoader
from langchain_community.tools import DuckDuckGoSearchResults
from typing_extensions import TypedDict
from langgraph.graph import StateGraph, START, END
from typing import Annotated
import operator
from langchain_community.chat_models import ChatZhipuAI
import os
import re
os.environ["ZHIPUAI_API_KEY"] = "YOUR_API_KEY"

class State(TypedDict):
    question: str
    answer: str
    context: Annotated[list, operator.add]

llm = ChatZhipuAI(model="glm-4-plus")

def search_web(state):
    """ 从网页搜索检索文档 """
    web_search_tool = DuckDuckGoSearchResults(max_results=3)
    search_docs = web_search_tool.invoke(state['question'])
    
    def extract_info(input_str):
        # 使用正则表达式匹配 snippet、title 和 link
        pattern = re.compile(r'snippet:\s*(.*?)\s*,\s*title:\s*(.*?)\s*,\s*link:\s*(.*?)\s*(?=snippet:|$)', re.DOTALL)
        matches = pattern.findall(input_str)
        
        result = []
        for match in matches:
            snippet, title, link = match
            result.append({
                "snippet": snippet.strip(),
                "title": title.strip(),
                "link": link.strip()
            })
        return result

    # 调用函数并打印结果
    search_docs = extract_info(str(search_docs))
    # 格式化
    formatted_search_docs = "\n\n---\n\n".join(
        [
            f'<Document href="{doc["link"]}"/>\n{doc["snippet"]}\n</Document>'
            for doc in search_docs
        ]
    )

    return {"context": [formatted_search_docs]} 

def search_wikipedia(state):
    """ 从Wikipedia检索文档 """
    search_docs = WikipediaLoader(query=state['question'], 
                                  load_max_docs=2).load()

    # 格式化
    formatted_search_docs = "\n\n---\n\n".join(
        [
            f'<Document source="{doc.metadata["source"]}" page="{doc.metadata.get("page", "")}"/>\n{doc.page_content}\n</Document>'
            for doc in search_docs
        ]
    )

    return {"context": [formatted_search_docs]} 

def generate_answer(state):
    """ Node to answer a question """
    context = state["context"]
    question = state["question"]

    answer_template = """Answer the question {question} using this context: {context}"""
    answer_instructions = answer_template.format(question=question, 
                                                       context=context)    
    answer = llm.invoke([SystemMessage(content=answer_instructions)]+[HumanMessage(content=f"Answer the question.")])

    return {"answer": answer}

# 增加节点
builder = StateGraph(State)

builder.add_node("search_web",search_web)
builder.add_node("search_wikipedia", search_wikipedia)
builder.add_node("generate_answer", generate_answer)

builder.add_edge(START, "search_wikipedia")
builder.add_edge(START, "search_web")
builder.add_edge("search_wikipedia", "generate_answer")
builder.add_edge("search_web", "generate_answer")
builder.add_edge("generate_answer", END)
graph = builder.compile()

display(Image(graph.get_graph().draw_mermaid_png()))

result = graph.invoke({"question": "How were Nvidia's Q2 2024 earnings"})
print(result['answer'].content)

# "Nvidia's Q2 2024 earnings were exceptionally strong. The company reported a record quarterly revenue of $30.0 billion, which represented a 15% increase from the previous quarter (Q1) and a significant 122% increase from the same period a year ago. A major highlight was the data center revenue, which soared to $26.3 billion, marking a 16% increase from Q1 and a staggering 154% increase year-over-year.\n\nAdditionally, earnings per share came in at $0.67, up 168% from the previous year. This performance exceeded analyst expectations, as polled by FactSet, which had anticipated revenue of $28.72 billion and earnings of $0.65 per share. Furthermore, Nvidia projected that revenue for the current quarter would reach $32.5 billion, surpassing the analyst consensus.\n\nOverall, these results underscored Nvidia's robust growth and strong market position, particularly in the data center segment, driven by the increasing demand for AI hardware and software. The company's CEO expressed optimism about the future of AI use and Nvidia's role in reequipping the world's data centers, indicating a positive outlook for continued growth."
```

### 4. Map & Reduce（Module 4-3）

![image-20241119212720437](./LangGraph教程.assets/image-20241119212720437.png)

![image-20241119212747209](./LangGraph教程.assets/image-20241119212747209.png)

```python
import os
os.environ["ZHIPUAI_API_KEY"] = "YOUR_API_KEY"

from langchain_community.chat_models import ChatZhipuAI

# Prompts we will use
subjects_prompt = """Generate a list of 3 sub-topics that are all related to this overall topic: {topic}."""
joke_prompt = """Generate a joke about {subject}"""
best_joke_prompt = """Below are a bunch of jokes about {topic}. Select the best one! Return the ID of the best one, starting 0 as the ID for the first joke. Jokes: \n\n  {jokes}"""

# LLM
model = ChatZhipuAI(model="glm-4-plus")

import operator
from typing import Annotated
from typing_extensions import TypedDict
from pydantic import BaseModel

class Subjects(BaseModel):
    subjects: list[str]

class BestJoke(BaseModel):
    id: int
    
class OverallState(TypedDict):
    topic: str
    subjects: list
    jokes: Annotated[list, operator.add]
    best_selected_joke: str

def generate_topics(state: OverallState):
    prompt = subjects_prompt.format(topic=state["topic"])
    response = model.with_structured_output(Subjects).invoke(prompt)
    return {"subjects": response.subjects}

from langgraph.constants import Send
def continue_to_jokes(state: OverallState):
    # 我们将返回一个`Send`对象的列表，每个Send对象由图中的一个节点的名称以及发送到该节点的状态组成
    return [Send("generate_joke", {"subject": s}) for s in state["subjects"]]


class JokeState(TypedDict):
    subject: str

class Joke(BaseModel):
    joke: str

def generate_joke(state: JokeState):
    prompt = joke_prompt.format(subject=state["subject"])
    response = model.with_structured_output(Joke).invoke(prompt)
    return {"jokes": [response.joke]}

def best_joke(state: OverallState):
    jokes = "\n\n".join(state["jokes"])
    prompt = best_joke_prompt.format(topic=state["topic"], jokes=jokes)
    response = model.with_structured_output(BestJoke).invoke(prompt)
    return {"best_selected_joke": state["jokes"][response.id]}

from IPython.display import Image
from langgraph.graph import END, StateGraph, START

# 构建图：在这里我们将所有内容放在一起以构建我们的图
graph = StateGraph(OverallState)
graph.add_node("generate_topics", generate_topics)
graph.add_node("generate_joke", generate_joke)
graph.add_node("best_joke", best_joke)
graph.add_edge(START, "generate_topics")
graph.add_conditional_edges("generate_topics", continue_to_jokes, ["generate_joke"])
graph.add_edge("generate_joke", "best_joke")
graph.add_edge("best_joke", END)

# 编译图
app = graph.compile()
Image(app.get_graph().draw_mermaid_png())


# 调用图：在这里我们调用它来生成一系列笑话
for s in app.stream({"topic": "汽车"}):
    print(s)
# {'generate_topics': {'subjects': ['汽车维护', '新能源汽车', '汽车设计']}}
# {'generate_joke': {'jokes': ['为什么汽车设计师总是很冷静？因为他们总是处理异常！']}}
# {'generate_joke': {'jokes': ['新能源汽车为什么不喜欢吃油？因为它更爱电饭煲！']}}
# {'generate_joke': {'jokes': ['为什么修车师傅总是那么冷静？因为他们每天都在处理异常！']}}
# {'best_joke': {'best_selected_joke': '新能源汽车为什么不喜欢吃油？因为它更爱电饭煲！'}}

```





