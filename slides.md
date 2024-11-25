---
# You can also start simply with 'default'
theme: seriph
# random image from a curated Unsplash collection by Anthony
# like them? see https://unsplash.com/collections/94734566/slidev
background: https://images.unsplash.com/photo-1568983268695-74a04650c8b3?ixlib=rb-4.0.3&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1470&q=80
# some information about your slides (markdown enabled)
title: Welcome to Slidev
info: |
  ## Slidev Starter Template
  Presentation slides for developers.

  Learn more at [Sli.dev](https://sli.dev)
# apply unocss classes to the current slide
class: text-center
# https://sli.dev/features/drawing
drawings:
  persist: false
# slide transition: https://sli.dev/guide/animations.html#slide-transitions
transition: slide-left
# enable MDC Syntax: https://sli.dev/features/mdc
mdc: true
---

# AI 背景下的特种兵打造

将个体效率极大提升，一人挑战一个队

---
layout: image
image: https://zk-feisu-file-platform-pub-prod-oss.obsv3.zj-zkr-1.zeekrlife.com/frontend-files/1/67440494e4b04d775767b0e2.png
backgroundSize: contain
---

<!--
The last comment block of each slide will be treated as slide notes. It will be visible and editable in Presenter Mode along with the slide. [Read more in the docs](https://sli.dev/guide/syntax.html#notes)
-->

---
transition: fade-out
layout: image-right
image: https://images.unsplash.com/photo-1662581871625-7dbd3ac1ca18?ixlib=rb-4.0.3&ixid=MnwxMjA3fDF8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=686&q=80
---
## 目录

- 现成的工具
  - 日常问答
  - 开发工具
  - 写作工具
- 搭建自己的工具
  - 搭建平台
  - 手撕一个
- 提示词
- Agent
  - Agent 概念
  - 虚拟团队-蜂群战略
- 总结

---
transition: slide-up
level: 2
---

# 日常问答

- 门户网站： [小智](https://x.zeekrlife.com)
- 嵌入到系统里的入口： [敏捷平台](https://agilemp.zeekrlife.com/)
- Native工具：豆包, OpenAI


---
transition: slide-up
level: 2
---

# 开发工具

- VScode里的一些插件
- Cursor编辑器
- 成熟产品
  - [v0](https://v0.dev/)
  - [bolt.new](https://bolt.new/)


---
transition: slide-up
level: 2
---

# 写作工具

- Notion
- Obsidian


---
transition: slide-up
level: 2
---

# 搭建自己的工具

- [智能体搭建平台](https://x.zeekrlife.com/agents)
- 手写一个


[openai](https://platform.openai.com/docs/api-reference/chat/create)

### 基础问答

```javascript
import OpenAI from 'openai';

const client = new OpenAI({
  apiKey: process.env['OPENAI_API_KEY'], // This is the default and can be omitted
});

async function main() {
  const chatCompletion = await client.chat.completions.create({
    messages: [{ role: 'user', content: 'Say this is a test' }],
    model: 'gpt-4o',
  });
}

main();

```

---
transition: slide-up
level: 2
---

# 搭建自己的工具
### 手写进阶

- Rag: 私有知识库
- Agent: 任务计划与执行


---
transition: slide-up
level: 2
---

# Agent
任务规划，与执行，可以简单的理解为一个 LLM(大脑) + 工具集(专业技能) + 执行器(运行环境)。

任务的描述使用工具，工具就是一个函数

<div grid="~ cols-2 gap-2" m="t-2">

```javascript
async function getCurrentWeather(latitude, longitude) {
  const url = `https://api.open-meteo.com/v1/forecast?latitude=${latitude}&longitude=${longitude}&hourly=apparent_temperature`;
  const response = await fetch(url);
  const weatherData = await response.json();
  return weatherData;
}

async function getLocation() {
  const response = await fetch("https://ipapi.co/json/");
  const locationData = await response.json();
  return locationData;
}
```

<div style="overflow-y: scroll; height: 350px">

``` javascript
const tools = [
  {
    type: "function",
    function: {
      name: "getCurrentWeather",
      description: "Get the current weather in a given location",
      parameters: {
        type: "object",
        properties: {
          latitude: {
            type: "string",
          },
          longitude: {
            type: "string",
          },
        },
        required: ["longitude", "latitude"],
      },
    }
  },
  {
    type: "function",
    function: {
      name: "getLocation",
      description: "Get the user's location based on their IP address",
      parameters: {
        type: "object",
        properties: {},
      },
    }
  },
];
```
</div>
</div>


---
transition: slide-up
level: 2
---

# 多Agent
Agent 群


把每个 Agent 理解为一个职能角色的工作者。

如果再加上一个工作调度者 Agent？

---
transition: slide-up
level: 2
layout: image
image: https://www.developerscantina.com/p/semantic-kernel-multiagents/cover_hu2b89fa2d576fd81acd9ff74385103be4_3830700_800x0_resize_box_3.png
---
# 虚拟团队
元宇宙？


---
level: 2
---
# 提示词
与大模型交互的唯一方式


![图片](https://cdn.prod.website-files.com/63e677cf5f9ef0afdbe871b8/64cac23d5107eb3c60973590_Prompt%20Engineering%20101%20-%20Promptitude.io%20-%20Structure.webp)


---
level: 2
---
# 提示词
与大模型交互的唯一方式


[提示词大全](https://www.promptingguide.ai/)


---
level: 2
---
# 总结
如何拥抱 AI

* 拓展个人能力边界，提升效率
* 工具很多，注意甄选
* 不要被 AI 带歪了：
  * 比如接触一个未知领域，大的框架的东西也要自己去研究好才能用好AI
  * 并不是万能的，很多知识体系还是需要自己去积累


---
transition: slide-up
level: 2
layout: image
image: https://zk-feisu-file-platform-pub-prod-oss.obsv3.zj-zkr-1.zeekrlife.com/frontend-files/1/67442e8de4b01367666a74cc.png
backgroundSize: contain
---
