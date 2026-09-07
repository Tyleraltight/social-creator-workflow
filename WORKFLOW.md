# Social Creator Workflow Specification

## 元数据
- **ID**: `social-creator-flow`
- **版本**: `1.0.0`
- **适用场景**: 微信公众号长文、小红书图文/笔记、短视频口播/B-roll/字幕
- **核心原则**: 情报先行、结构去AI味、事实可验证、交付即成片

---

## 步骤 1: 全域情报侦察 (Intelligence Recon)
1. 解析用户输入的平台（xhs / bilibili / douyin / wechat）及核心关键词。
2. 调度 MCP 工具：
   - `xiaohongshu_search` 获取高点赞/收藏笔记元数据。
   - `xiaohongshu_comments` 抓取真实互动评论，提炼高频槽点。
   - `bilibili_search` 了解长视频维度的核心切入角度。
3. 产出《受众痛点分析表》，包含：3个核心诉求、2个行业普遍吐槽、1个最具争议的反常识论点。

---

## 步骤 2: 商业定位与对标过滤 (Benchmarking)
1. 运行 `/dbs-benchmark` 审查竞品对标案例，剔除不可复现的个案。
2. 运行 `/dbs-diagnosis` 确立单篇内容的人设语调、目标读者阶段（小白入门 / 进阶实操 / 决策者视角）。
3. 确立单篇价值兑现承诺（Value Proposition）。

---

## 步骤 3: 深度起草与架构级洗 AI 味 (Drafting & De-AI)
1. **起草**:
   - 长文：执行 `khazix-writer` 叙事原型起草。
   - 短视频/图文：执行 `dbs-hook`（前20秒设计）与 `dbs-xhs-title`（75个爆款标题库）。
2. **Sepia 架构级洗稿**:
   - 执行 `sepia-review` 进行结构与指纹体检。
   - 执行 `sepia-refactor` 或 `sepia-recreate`：
     - 去除末尾所有道德式升华与抽象大道理。
     - 植入至少一个具体的失败试验或无效路径。
     - 打破等长句子律动，段落内交替使用短句与长句。
3. **事实边界终审**:
   - 运行 `oil-tone` 审查（`tone_lint.py`），去除任何缺乏事实依据的定性形容词，保持平铺直叙。

---

## 步骤 4: 工业级装配交付 (Production & Packaging)
1. **公众号图文**:
   - 调用 `gzh-design` 注入摸鱼绿或石墨排版规范。
   - 运行 `validate_gzh_html.py` 完成排版自检，输出独立 HTML 预览页。
2. **视觉物料**:
   - 科技实操：调用 `oil-cover` 自动完成视频抽帧并加盖官方 Logo。
   - 极简杂志风：调用 `gc-minimal-zine-poster` 输出日系排版图。
3. **视频与字幕**:
   - 动效视频：调用 `video-shotcraft` 运行 Remotion 2.5D 运镜组件。
   - 智能字幕：调用 `oil-subtitle`，通过百炼 FunAudio ASR 与 Qwen 3.7 视觉核验，输出无错别字字幕文件并压制成片。

---

## 步骤 5: 资产归档 (Compounding)
1. 运行 `/dbs-save` 将本次经验、对标模式归档至本地知识体系。
2. 更新专有名词词典与错题本。
