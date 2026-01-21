# Tiny-LLM Learning Project

A structured learning project for understanding LLM inference and serving systems by building a simplified vLLM from scratch, following the [tiny-llm course](https://skyzh.github.io/tiny-llm).

## 📚 About This Project

This repository documents my journey learning how Large Language Models work internally, specifically focusing on:

- **LLM Architecture**: Attention mechanisms, RoPE, GQA, normalization
- **Inference Optimization**: KV caching, flash attention, continuous batching
- **Systems Engineering**: Custom kernels, quantization, serving infrastructure
- **Practical Implementation**: Building components from scratch using matrix operations

## 🎯 Learning Objectives

### Week 1: From Matmul to Text (7 days)
Build a complete Qwen2 model from scratch:
- [ ] Day 1.1: Attention and Multi-Head Attention
- [ ] Day 1.2: Positional Encodings and RoPE
- [ ] Day 1.3: Grouped/Multi Query Attention
- [ ] Day 1.4: RMSNorm and MLP
- [ ] Day 1.5: The Qwen2 Model
- [ ] Day 1.6: Generating the Response
- [ ] Day 1.7: Sampling and Preparing for Week 2

### Week 2: Tiny vLLM (8+ days)
Implement efficient inference infrastructure:
- [ ] Day 2.1: Key-Value Cache
- [ ] Day 2.2-2.3: Quantized Matmul (C++/Metal kernels)
- [ ] Day 2.4-2.5: Flash Attention implementation
- [ ] Day 2.6-2.7: Continuous Batching

### Week 3: Advanced Serving (TBD)
Production-ready serving techniques:
- [ ] Paged Attention
- [ ] Mixture of Experts (MoE)
- [ ] Speculative Decoding
- [ ] RAG Pipeline
- [ ] Tool Calling
- [ ] Long Context Handling

## 📁 Repository Structure

```
.
├── sessions/           # Daily learning session documentation
│   ├── week1/         # Week 1 sessions
│   ├── week2/         # Week 2 sessions
│   └── week3/         # Week 3 sessions
├── code/              # Implementation code
│   ├── week1/         # Week 1 implementations
│   ├── week2/         # Week 2 implementations
│   └── week3/         # Week 3 implementations
├── notes/             # Learning notes and concepts
├── exercises/         # Practice exercises and experiments
├── progress/          # Progress tracking and planning
├── CLAUDE.md          # AI tutor instructions (Socratic method)
├── SESSION-TEMPLATE.md # Template for daily sessions
└── requirements.txt   # Python dependencies
```

## 🚀 Getting Started

### Prerequisites

- Python 3.9+
- Apple Silicon Mac (for MLX) or CUDA-capable GPU
- Basic understanding of deep learning and PyTorch
- Linear algebra fundamentals

### Setup

```bash
# Clone the repository
git clone <your-repo-url>
cd ailearn-tiny-llm

# Create virtual environment
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt

# Download Qwen2 models (will be set up later)
# Instructions in Week 1 Day 1
```

## 📖 Learning Approach

This project follows a **Socratic learning method** with AI guidance:

1. **Study** the tiny-llm course material for each day
2. **Implement** the concepts from scratch
3. **Document** your understanding in daily sessions
4. **Practice** with exercises and experiments
5. **Review** with AI tutor (Claude) using CLAUDE.md instructions

### Daily Session Flow

1. Read the course material
2. Create a new session document from SESSION-TEMPLATE.md
3. Implement the day's components in `/code`
4. Document learnings, challenges, and insights
5. Update progress tracker
6. Test and validate implementation

## 📊 Progress Tracking

Track your progress in `/progress/tiny-llm-tracker.md`:
- Topics covered and mastery level
- Implementation status
- Knowledge gaps identified
- Time spent on each component
- Blockers and solutions

## 🎓 Learning Resources

- **Course Website**: https://skyzh.github.io/tiny-llm
- **Original Repo**: https://github.com/skyzh/tiny-llm
- **Reference Implementation**: Check course repo for hints
- **MLX Documentation**: https://ml-explore.github.io/mlx/

## 🤝 AI-Assisted Learning

This project uses Claude as an AI tutor following the Socratic method:
- Ask guiding questions rather than providing direct answers
- Encourage thinking through problems independently
- Validate understanding through dialogue
- See `CLAUDE.md` for detailed tutor instructions

## 📝 Documentation Standards

Each session should include:
- **Concepts Learned**: Key theoretical concepts
- **Implementation Details**: Code explanations
- **Challenges Faced**: Problems encountered and solutions
- **Insights**: Deeper understanding gained
- **Next Steps**: What to focus on next

## 🛠️ Tech Stack

- **MLX**: Apple Silicon-optimized ML framework
- **Python**: Primary implementation language
- **C++/Metal**: Custom kernels for optimization
- **NumPy**: Matrix operations
- **PyTorch**: Reference for concepts (not used in implementation)

## 📅 Timeline

- **Week 1**: 7 days (Qwen2 model implementation)
- **Week 2**: 8+ days (Inference optimization)
- **Week 3**: TBD (Advanced serving)
- **Total**: ~3-4 weeks of focused learning

## 🎯 Success Criteria

- [ ] Complete Qwen2 model implementation from scratch
- [ ] Implement efficient KV caching
- [ ] Build custom quantization kernels
- [ ] Implement flash attention
- [ ] Create continuous batching system
- [ ] Understand trade-offs in LLM serving
- [ ] Document all learnings comprehensively

## 📄 License

This is a personal learning project. Course materials belong to the original tiny-llm project.

## 🙏 Acknowledgments

- **[Alex Chi (skyzh)](https://github.com/skyzh)** for creating the excellent [tiny-llm course](https://github.com/skyzh/tiny-llm) and comprehensive learning materials
- **[CFP-study project](https://github.com/chenran818/CFP-study)** by chenran818 for inspiring this structured learning approach and Socratic teaching methodology
- The open-source LLM community for advancing accessible AI education

---

Happy Learning! 🚀
