# wings-claude-skills

个人维护的 Claude Code 技能（Skill）集合，兼容 Claude Code Plugin Marketplace。

## Skill 列表

| Skill | 路径 | 描述 |
| ----- | ---- | ---- |
| *暂无* | — | 添加第一个 skill 后更新此表 |

## Plugin 列表

| Plugin | 安装名 | 描述 | 包含内容 |
| ------ | ------ | ---- | -------- |
| *暂无* | — | — | — |

## 安装使用

### 方式一：Claude Code Plugin

```bash
# 1. 添加插件市场源（仅首次）
claude plugin marketplace add git@github.com:Wingsdh/wings-claude-skills.git

# 2. 安装插件
claude plugin install <plugin-name>@wings-claude-skills
```

### 方式二：npx skills

```bash
# 安装所有技能
npx skills add git@github.com:Wingsdh/wings-claude-skills.git

# 安装单个技能
npx skills add git@github.com:Wingsdh/wings-claude-skills.git --skill <skill-name>
```

## 目录结构

```
wings-claude-skills/
├── .claude-plugin/           # Marketplace 主配置
│   └── marketplace.json
├── skills/                   # 技能源文件目录
├── plugins/                  # 插件目录（通过符号链接组装 skill）
└── docs/                     # 文档资源
```

## 添加新技能

1. 在 `skills/` 下创建技能目录（如 `skills/my-skill/`）
2. 添加 `SKILL.md`（技能定义）和 `README.md`（使用说明）
3. 本地调试：`npx skills add ./skills/my-skill`
4. 更新本 README 的 Skill 列表
5. 如需打包为 Plugin，在 `plugins/` 下创建插件目录并用符号链接引入

## 创建新插件

1. 在 `plugins/` 下新建目录，创建 `.claude-plugin/plugin.json`
2. 用符号链接引入 skill：`cd plugins/<name>/skills && ln -s ../../../skills/<skill> <skill>`
3. 在 `.claude-plugin/marketplace.json` 的 `plugins` 数组中注册
4. 递增 `marketplace.json` 的 `metadata.version`
