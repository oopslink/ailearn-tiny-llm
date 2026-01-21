# 项目概览 / Project Overview

## 🎯 项目目标 / Project Goals

这是一个结构化的学习项目，通过从头构建简化版 vLLM 来深入理解大语言模型（LLM）推理和服务系统。

This is a structured learning project for understanding LLM inference and serving systems by building a simplified vLLM from scratch.

## 📚 学习资源 / Learning Resources

- **课程网站 / Course Site**: https://skyzh.github.io/tiny-llm
- **原始仓库 / Original Repo**: https://github.com/skyzh/tiny-llm
- **参考项目 / Reference Project**: https://github.com/chenran818/CFP-study

## 🗂️ 项目结构 / Project Structure

```
ailearn-tiny-llm/
│
├── 📖 README.md                 # 项目主文档 / Main documentation
├── 🤖 AGENTS.md                 # AI助手指南 / AI agent guide
├── 🎓 CLAUDE.md                 # 苏格拉底式教学指南 / Socratic teaching guide
├── 📋 SESSION-TEMPLATE.md       # 学习会话模板 / Session template
├── 🤝 CONTRIBUTING.md           # 贡献指南 / Contributing guide
├── 📦 requirements.txt          # Python依赖 / Python dependencies
│
├── 📚 sessions/                 # 学习会话文档 / Learning session docs
│   ├── week1/                   # 第一周：从矩阵运算到文本 / Week 1: Matmul to Text
│   ├── week2/                   # 第二周：Tiny vLLM / Week 2: Tiny vLLM
│   └── week3/                   # 第三周：高级服务 / Week 3: Advanced Serving
│
├── 💻 code/                     # 代码实现 / Code implementations
│   ├── week1/                   # 第一周代码 / Week 1 code
│   ├── week2/                   # 第二周代码 / Week 2 code
│   └── week3/                   # 第三周代码 / Week 3 code
│
├── 📝 notes/                    # 学习笔记 / Learning notes
├── 🧪 exercises/                # 练习题 / Practice exercises
└── 📊 progress/                 # 进度追踪 / Progress tracking
    └── tiny-llm-tracker.md      # 主进度追踪表 / Main progress tracker
```

## 🚀 快速开始 / Quick Start

### 1. 环境设置 / Environment Setup

```bash
# 创建虚拟环境 / Create virtual environment
python -m venv venv
source venv/bin/activate  # Windows: venv\Scripts\activate

# 安装依赖 / Install dependencies
pip install -r requirements.txt
```

### 2. 开始学习 / Start Learning

1. 阅读 `README.md` 了解整体项目
2. 查看 `sessions/week1/README.md` 开始第一周
3. 使用 `SESSION-TEMPLATE.md` 记录每日学习
4. 在 `code/week1/` 实现代码
5. 更新 `progress/tiny-llm-tracker.md` 追踪进度

**English:**
1. Read `README.md` for project overview
2. Check `sessions/week1/README.md` to start Week 1
3. Use `SESSION-TEMPLATE.md` for daily session docs
4. Implement code in `code/week1/`
5. Update `progress/tiny-llm-tracker.md` to track progress

## 📅 学习路线 / Learning Path

### 第一周 / Week 1: 从矩阵运算到文本 (7天)
构建完整的 Qwen2 模型

Building complete Qwen2 model
- 注意力机制 / Attention mechanisms
- 位置编码 / Positional encodings
- 模型架构 / Model architecture
- 文本生成 / Text generation

### 第二周 / Week 2: Tiny vLLM (8+天)
实现高效推理优化

Implementing efficient inference optimizations
- KV 缓存 / KV caching
- 量化 / Quantization
- Flash Attention
- 连续批处理 / Continuous batching

### 第三周 / Week 3: 高级服务 (6+天)
生产级特性

Production-ready features
- 分页注意力 / Paged attention
- 专家混合 / Mixture of Experts
- 推测解码 / Speculative decoding
- RAG 和 Agent / RAG and Agents

## 🎓 学习方法 / Learning Approach

本项目采用**苏格拉底式学习法**配合 AI 导师指导：

This project follows the **Socratic learning method** with AI tutor guidance:

1. **自主思考** / Think independently
2. **提出问题** / Ask questions
3. **实践实现** / Implement hands-on
4. **反思总结** / Reflect and document
5. **AI 引导** / AI-guided discovery

详见 `CLAUDE.md` 了解 AI 导师如何帮助你学习。

See `CLAUDE.md` for how AI tutors guide your learning.

## 📊 进度追踪 / Progress Tracking

使用 `progress/tiny-llm-tracker.md` 追踪：

Track using `progress/tiny-llm-tracker.md`:
- ✅ 已完成主题 / Completed topics
- 🟡 进行中主题 / In-progress topics
- ⬜ 待开始主题 / Pending topics
- ⭐ 精通程度 / Mastery level
- ⏱️ 投入时间 / Time invested

## 💡 重要文档说明 / Key Document Descriptions

| 文档 / Document | 用途 / Purpose |
|----------------|---------------|
| `README.md` | 项目总览和入门指南 / Project overview and getting started |
| `AGENTS.md` | AI 助手的工作指南（**为未来 AI 准备**）/ AI agent guide (**for future AI**) |
| `CLAUDE.md` | 苏格拉底式教学方法说明 / Socratic teaching methodology |
| `SESSION-TEMPLATE.md` | 每日学习会话的模板 / Template for daily sessions |
| `progress/tiny-llm-tracker.md` | 详细的进度追踪表 / Detailed progress tracker |
| `sessions/weekX/README.md` | 每周学习目标和指南 / Weekly objectives and guide |
| `code/README.md` | 代码实现指南 / Code implementation guide |

## 🎯 成功标准 / Success Criteria

完成本项目后，你将能够：

After completing this project, you will be able to:

- ✅ 从零实现 LLM 推理系统 / Implement LLM inference from scratch
- ✅ 深入理解注意力机制 / Deeply understand attention mechanisms
- ✅ 编写自定义 CUDA/Metal 内核 / Write custom CUDA/Metal kernels
- ✅ 理解服务系统权衡 / Understand serving system trade-offs
- ✅ 调试复杂 ML 系统 / Debug complex ML systems
- ✅ 优化性能 / Optimize for performance
- ✅ 阅读 vLLM 源代码 / Read vLLM source code
- ✅ 为 LLM 服务项目贡献代码 / Contribute to LLM serving projects

## 🤝 如何使用 AI 助手 / How to Use AI Assistants

1. **提问而非索要答案** / Ask questions, don't ask for answers
2. **先自己思考** / Think independently first
3. **使用 AI 验证理解** / Use AI to validate understanding
4. **引导式学习** / Learn through guidance
5. **记录见解** / Document insights

AI 助手会遵循 `CLAUDE.md` 中的苏格拉底式方法，通过提问引导你发现答案。

AI assistants follow Socratic method in `CLAUDE.md`, guiding you to discover answers through questions.

## 📖 推荐阅读顺序 / Recommended Reading Order

1. ✅ 本文件 / This overview
2. 📖 `README.md` - 完整项目介绍 / Full project introduction
3. 🎓 `CLAUDE.md` - 了解学习方法 / Understand learning approach
4. 📚 `sessions/week1/README.md` - 开始第一周 / Start Week 1
5. 📋 `SESSION-TEMPLATE.md` - 学习如何记录 / Learn how to document
6. 📊 `progress/tiny-llm-tracker.md` - 了解追踪系统 / Understand tracking system

## 🌟 项目亮点 / Project Highlights

- ✨ **系统化学习路径** / Systematic learning path
- 🎯 **实践导向** / Hands-on focused
- 📝 **详细文档** / Comprehensive documentation
- 🤖 **AI 辅助学习** / AI-assisted learning
- 📊 **进度追踪** / Progress tracking
- 🧪 **练习和实验** / Exercises and experiments

## 🙏 致谢 / Acknowledgments

- **Alex Chi (skyzh)** - 创建优秀的 tiny-llm 课程 / Creating excellent tiny-llm course
- **CFP-study 项目** - 启发学习结构设计 / Inspiring learning structure design
- **开源社区** / Open source community

---

**开始学习日期 / Start Date**: [填写你的开始日期 / Fill in your start date]  
**目标完成日期 / Target Completion**: [填写目标日期 / Fill in target date]  
**当前状态 / Current Status**: 设置阶段 / Setup Phase

祝学习愉快！🚀 / Happy Learning! 🚀
