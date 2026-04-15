# 骑士精神 (Chivalry)

一个开源的「骑士精神 skill」套件，主兼容 Claude Code，同时提供 Cursor 和 Codex 的现成适配。

它判断的不是你有没有演得像中世纪角色扮演玩家。
它判断的是：你这件事到底有没有荣誉、分寸、勇气、怜悯和体面。

[English](README.md) | 简体中文

## 兼容性

| 工具 | 状态 | 接入方式 |
| --- | --- | --- |
| Claude Code | 原生最佳支持 | `plugins/chivalry/skills/chivalry/` |
| Cursor | 已适配 | `.cursor/rules/chivalry.mdc` |
| Codex | 已适配 | 仓库根目录 `AGENTS.md` |

## 它是干什么的

这个 skill 会看一段话、一个决定、一个关系局面，然后回答两个问题：

1. 这件事算不算符合骑士精神？
2. 如果不够体面，更像一个真正骑士的做法是什么？

它适合现代场景：冲突、拒绝、道歉、领导、忠诚两难、恋爱关系、围观者困境、公开发言、报复冲动、权力不对称、信任修复。

## 这玩意儿最有意思的地方在哪

无聊版本的“美德 skill”会变成说教机器人。
真正好玩的版本，一定要有张力。

重点根本不是“礼貌”。
重点是这些东西彼此会打架：

- 忠诚 vs 正义
- 勇气 vs 审慎
- 怜悯 vs 问责
- 礼貌 vs 直言
- 爱慕 vs 同意
- 服务 vs 自我尊重

只有这些价值互相顶牛，这个 skill 才有戏，不然就是一锅寡淡鸡汤。

## 它的核心判法

这个 skill 用七个维度裁决：

- **誓言 Oath** —— 你有没有守诺、守责、守承诺后的代价？
- **勇气 Courage** —— 你有没有扛该扛的，而不是缩在舒服区？
- **怜悯 Mercy** —— 你有没有避免不必要的羞辱和残忍？
- **礼貌 Courtesy** —— 你有没有保住对方的基本体面，尤其在公开场合？
- **护弱 Protection** —— 你有没有保护更脆弱、更暴露的一方？
- **荣誉 Honor** —— 你的手段是否光明、公正、不耍小聪明？
- **节制 Measure** —— 你是在克制自己，还是让 ego 开车？

## 它明确反对什么

这个 skill 会直接拆穿“伪骑士精神”：

- 把占有欲包装成保护
- 把嫉妒包装成忠贞
- 为了 ego 打架还叫勇气
- 为了博掌声去“英雄救美”
- 当众羞辱别人还说自己只是诚实
- 搞巨大的恩情表演让别人欠你
- 性别傲慢、爹味控制、跟踪、胁迫、报复表演

一句话：同意、法律、安全、基本尊严，比任何花哨姿态都更优先。

## 目录结构

```text
chivalry/
├── .cursor/
│   └── rules/
│       └── chivalry.mdc
├── .claude-plugin/
│   └── marketplace.json
├── AGENTS.md
├── README.md
├── README.zh-CN.md
├── VERSION
└── plugins/
    └── chivalry/
        ├── .claude-plugin/
        │   └── plugin.json
        └── skills/
            └── chivalry/
                ├── SKILL.md
                ├── principles.md
                ├── scenarios.md
                └── examples.md
```

## 怎么用

### 方式一：直接当独立 skill 用

把下面这个目录：

```text
plugins/chivalry/skills/chivalry/
```

复制到：

```text
~/.claude/skills/chivalry/
```

然后直接用：

```text
/chivalry 你的场景
```

这是最爽的用法，命令短，不绕。

### 方式二：本地当插件调试

```bash
claude --plugin-dir ./plugins/chivalry
```

然后用：

```text
/chivalry:chivalry 你的场景
```

### 方式三：发布成 marketplace

把这个仓库推到 GitHub 或其他 git 平台后：

```bash
claude plugin marketplace add <你的仓库>
claude plugin install chivalry@chivalry-tools
```

然后用：

```text
/chivalry:chivalry 我为了立威，当众把下属骂了一顿，这算骑士精神吗？
```

### 方式四：在 Cursor 里用

把下面这个文件复制到目标项目的 `.cursor/rules/` 目录：

```text
.cursor/rules/chivalry.mdc
```

然后直接在 Cursor 聊天里问，例如：

```text
这到底算骑士精神，还是只是把虚荣包装成美德？
```

### 方式五：在 Codex 里用

把仓库根目录的 `AGENTS.md` 复制到你的项目根目录，或者把其中的 Chivalry 部分合并进你现有的 `AGENTS.md`。

然后直接在 Codex 里问，例如：

```text
帮我用骑士精神的标准判断一下这段道歉文案。
```

## 适合测试的输入

- “我答应帮忙，现在反悔了，怎样才算体面？”
- “老板让我背锅，我该不该为了忠诚忍了？”
- “我当众怼了别人，因为他活该，这算荣誉吗？”
- “有人被嘲笑，我没出声，这算不算怯懦？”
- “约会三次后直接消失，算不算不体面？”
- “我想以保护为名查看伴侣和谁聊天，这算骑士精神还是控制欲？”
- “这算不算骑士精神？”
- “一个体面的骑士在这种局面下会怎么做？”

## 输出风格

它不会给你装模作样打 82 分。
直接判：

- Knightly
- Passable
- Unknightly
- Base
- Craven

典型输出像这样：

```text
Verdict: Unknightly
Herald's line: 你维护的不是荣誉，是面子。
Passed or failed tests: Mercy, Courtesy, Measure
The more knightly move:
1. 先修复你公开造成的伤害。
2. 私下直说问题，不再当众演示权力。
3. 把“立威”换成“担责”。
Words you can use:
“问题我还是认定有，但我刚才的方式不体面。我来把它修正。”
If already done, penance:
“当天内补救。拖久了就不是修复，是装死。”
```

## 你可以往哪几个方向继续玩

1. **更亚瑟王**：更浪漫、更仪式、更有传奇味。
2. **更现代实用**：减少戏剧腔，强化职场和亲密关系建议。
3. **更狠**：对虚荣、怯懦、滥用地位判得更重。

我现在给你的版本，是“能落地，又有一点圆桌法庭味道”。

## 我的判断

这类 skill 最容易做废的方式，就是做成“礼貌建议器”。
那太没劲了。

它真正该有的锋芒是敢直接说：

- “这不是高贵，这是虚荣。”
- “这不是保护，这是控制。”
- “这不是勇气，这是表演。”
- “这不是善良，这是软弱。”

没这口气，这 skill 就死了。

## License

拿去用，拿去改，拿去拆。
别把牙都磨平就行。
