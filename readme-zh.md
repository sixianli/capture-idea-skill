# capture-idea skill for Codex CLI

## 安装

通常用户已经有 `~/.codex/skills/` 目录。这里要做的是在该目录下创建 `capture-idea/` 子目录，并把 skill 文件复制进去：

```bash
mkdir -p ~/.codex/skills/capture-idea
cp -r capture-idea/* ~/.codex/skills/capture-idea/
chmod +x ~/.codex/skills/capture-idea/scripts/capture_idea.py
```

## 目录结构

```
~/.codex/skills/capture-idea/
├── SKILL.md                      # Skill 指令文件（Codex 读取）
├── scripts/
│   └── capture_idea.py           # 确定性文件操作脚本
├── references/
│   ├── good-capture.md           # 正例
│   └── bad-capture.md            # 反例
└── tests/
    └── test_capture_idea.py      # 21 个 pytest 测试
```

运行后会生成：

```
<当前工作项目>/docs/ideas/
├── INDEX.md                      # 索引表
└── YYYY-MM-DD-<slug>.md          # 灵感档案
```

## 使用方式

在 Codex CLI 中触发：

```
$capture-idea
记录一下这个想法
记录我的灵感
记录我的创意
save this idea
```

手动运行脚本（dry-run 预览）：

```bash
# 在目标项目目录里执行
python ~/.codex/skills/capture-idea/scripts/capture_idea.py \
  --title "认知分层 profile 设计" \
  --core-ideas "- profile 不是用户事实档案，而是用户认知状态的分层快照" \
  --thought-trajectory "- 从平面记忆存储出发，转向区分稳定层和漂浮层" \
  --quotes '["有些认知是笃定的深度记忆，有些还在脑海的浅层漂荡", "profile 不能只做事实归档"]' \
  --open-questions "- 是否在 profile 中显式使用分层语言？" \
  --dry-run
```

## 运行测试

```bash
cd ~/.codex/skills/capture-idea
uv run --with pytest python -m pytest tests/ -v
```
