# 《骑士精神》副卷：导览与传度

> 若 [README.md](README.md) 是法典前页，此卷便只做一件事：替后来者指路。
> 它不重述整部铁律，只说明此卷为何存在、诸文件各司何职、以及该如何把它传到 Claude Code、Cursor 与 Codex。

## 此卷所司

`Chivalry / 骑士精神` 不是礼貌生成器，也不是替虚荣找台阶的温和顾问。
它受召时，只断两件事：

1. 此行是否合乎骑士精神。
2. 若不合，其人眼下更体面的下一步是什么。

若你想先读主卷的口气、边界与判词，请回到 [README.md](README.md)。
若你只想尽快装好、找对入口、知道仓内从哪里读起，就留在此卷。

## 诸门所在

| 载体 | 入口文件 | 用途 |
| --- | --- | --- |
| Claude Code | `plugins/chivalry/skills/chivalry/` | 技能正文与附卷 |
| Cursor | `.cursor/rules/chivalry.mdc` | 规则注入 |
| Codex | `AGENTS.md` | 代理指令入口 |

## 如何传度

### 一、作为独立技能抄入 Claude Code

将此目录：

```text
plugins/chivalry/skills/chivalry/
```

复制到：

```text
~/.claude/skills/chivalry/
```

随后可直接呼名：

```text
/chivalry 你的场景
```

### 二、在仓内本地调试 Claude 插件

```bash
claude --plugin-dir ./plugins/chivalry
```

随后使用：

```text
/chivalry:chivalry 你的场景
```

### 三、登记到 Claude Code Marketplace

将仓库推到 GitHub 或其他 git 平台后，可执行：

```bash
claude plugin marketplace add <你的仓库>
claude plugin install chivalry@chivalry-tools
```

随后可这样发问：

```text
/chivalry:chivalry 我为了立威，当众让同事难堪，这算骑士精神吗？
```

### 四、传至 Cursor

把下列文件复制到目标项目的 `.cursor/rules/` 目录：

```text
.cursor/rules/chivalry.mdc
```

然后在 Cursor 聊天中直接问案，例如：

```text
这到底算骑士精神，还是只是把虚荣包装成美德？
```

### 五、传至 Codex

将仓库根目录的 `AGENTS.md` 复制到目标项目根目录，或把其中的 Chivalry 段落并入你现有的 `AGENTS.md`。

随后可直接在 Codex 中发问，例如：

```text
帮我用骑士精神的标准判断一下这段道歉文案。
```

## 仓内读法

若你已进仓，通常按这条顺序就够：

- `README.md`：主卷前页，负责定调与立界。
- `AGENTS.md`：Codex 的入口说明。
- `.cursor/rules/chivalry.mdc`：Cursor 的规则文本。
- `plugins/chivalry/skills/chivalry/SKILL.md`：技能主卷。
- `plugins/chivalry/skills/chivalry/principles.md`：七重试炼与原则。
- `plugins/chivalry/skills/chivalry/scenarios.md`：常见局面。
- `plugins/chivalry/skills/chivalry/examples.md`：示例判词与输出风格。

## 可先试问的几案

- “我答应帮忙，现在反悔了，怎样退场才不失体面？”
- “我当众怼了别人，因为我觉得他活该，这算不算荣誉？”
- “有人被嘲笑，我没出声，这算不算怯懦？”
- “我想以保护为名查看伴侣和谁聊天，这是保护还是控制？”

## 许可

拿去用，拿去改，拿去拆。
别把牙都磨平就行。
