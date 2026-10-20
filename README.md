# qiqi-self-media-review

奇其的自媒体发布前统一审核 Skill。一个入口联合 DBS 的内容风险检查和 guoshen 的平台、音轨、字幕、全画面证据检查，最后提醒把同一份内容交给豆包独立复核。

## 使用

```text
用 $qiqi-self-media-review 审核这份文稿或视频。
```

用户只需要调用这一个 Skill，不需要分别调用 DBS 和 guoshen。

## 仓库结构

```text
qiqi-self-media-review/
├── SKILL.md
├── agents/openai.yaml
└── sources/
    ├── guoshen/   → qiqi-huang-ai/guoshen
    └── dbskill/   → qiqi-huang-ai/dbskill
```

`sources/` 使用 Git Submodule 保留两个项目各自的更新历史与许可证。本仓库的根 Skill 负责调度和合并结果，不复制 DBS 的受限许可内容。

## 克隆源码

查看包含两个来源仓库的完整源码：

```sh
git clone --recurse-submodules https://github.com/qiqi-huang-ai/qiqi-self-media-review.git
```

只使用统一入口时，安装根目录的 `SKILL.md` 和 `agents/`，并确保环境中已经安装 `dbs-content-risk-check` 与 `guoshen`。

## 许可

根目录的统一调度代码采用 MIT 许可。子模块继续适用各自许可证，详见 [THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md)。

DBS 上游采用 CC BY-NC 4.0；如果审核流程要用于收费服务、商业交付或其他商业场景，需要先取得相应许可，或者用不依赖 DBS 内容的自有规则重新实现该层。

本项目提供发布前风险参考，不连接平台内部审核，也不保证发布通过。
