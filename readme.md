# capture-idea Skill for Codex CLI

## Installation

Most users already have the `~/.codex/skills/` directory. The only setup needed here is to create the `capture-idea/` subdirectory under it and copy the skill files into place:

```bash
mkdir -p ~/.codex/skills/capture-idea
cp -r capture-idea/* ~/.codex/skills/capture-idea/
chmod +x ~/.codex/skills/capture-idea/scripts/capture_idea.py
```

## Directory Structure

```
~/.codex/skills/capture-idea/
├── SKILL.md                      # Skill instruction file read by Codex
├── scripts/
│   └── capture_idea.py           # Deterministic file operation script
├── references/
│   ├── good-capture.md           # Good example
│   └── bad-capture.md            # Bad example
└── tests/
    └── test_capture_idea.py      # 21 pytest tests
```

After running, the skill generates:

```
<current working project>/docs/ideas/
├── INDEX.md                      # Index table
└── YYYY-MM-DD-<slug>.md          # Idea note
```

## Usage

Trigger it in Codex CLI with:

```
$capture-idea
记录一下这个想法
记录我的灵感
记录我的创意
save this idea
```

Run the script manually for a dry-run preview:

```bash
# Run this inside the target project directory
python ~/.codex/skills/capture-idea/scripts/capture_idea.py \
  --title "认知分层 profile 设计" \
  --core-ideas "- profile 不是用户事实档案，而是用户认知状态的分层快照" \
  --thought-trajectory "- 从平面记忆存储出发，转向区分稳定层和漂浮层" \
  --quotes '["有些认知是笃定的深度记忆，有些还在脑海的浅层漂荡", "profile 不能只做事实归档"]' \
  --open-questions "- 是否在 profile 中显式使用分层语言？" \
  --dry-run
```

## Run Tests

```bash
cd ~/.codex/skills/capture-idea
uv run --with pytest python -m pytest tests/ -v
```
