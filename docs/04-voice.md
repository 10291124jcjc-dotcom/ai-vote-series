# 04 · 配音：用你自己的声音

原号作者是自己配音的。我们用声音克隆：录一段样本做一次克隆，以后每集的台词都用这个音色合成。

## 两种

| | 是什么 | 要什么 |
| --- | --- | --- |
| `volc`（推荐） | 火山引擎「声音复刻」，你自己的声音；中文克隆音色说英文也清楚（Day 1 演示就是） | 控制台复刻一次，把 `VOLC_API_KEY`、`VOLC_SPEAKER_ID`（S_ 开头）写进 `.env`（系列文件夹或任一上级目录，或 `~/.vote-series/.env`） |
| `edge`（占位） | edge-tts 免费 AI 声音，只用来先看样片 | 不要密钥 |

```bash
python scripts/voice.py EP --test "This is Leo."     # 先试一句
python scripts/voice.py EP                            # 整集：合成 + 去首尾静音 + 对齐每个词 + 嘴型
python scripts/voice.py EP --provider edge            # 没配密钥时占位
```

- 每句单独合成、有缓存：改哪句只重新合成哪句
- `faster-whisper`（CPU）对出每个词的时间，字幕和道具都卡这个时间；顺便用它听一遍：识别结果和台词对不上，多半是发音有问题，换个说法重合成
- `script.json` 里每句的 `gap` 是这句后面停多久；投票、揭晓前多停 0.5 秒

## 注意

- 密钥是你的，只放 `.env`，不要打印、不要提交到 GitHub（`.gitignore` 已经排除 `.env`）
- 国内平台发布要勾选「AI 生成 / 合成」声明；海外平台按各自规则标注
- 不要克隆别人的声音
