# Week 1: From Matmul to Text

This week focuses on building the complete Qwen2 language model from scratch using only matrix operations. By the end of this week, you'll have a working transformer model that can generate text.

## 📚 Overview

**Duration**: 7 days  
**Goal**: Implement a complete Qwen2 model from basic building blocks  
**Approach**: Bottom-up - start with attention mechanism and build to full model

## 🎯 Learning Objectives

By the end of Week 1, you should be able to:

- ✅ Implement scaled dot product attention from scratch
- ✅ Build multi-head attention and its variants (GQA, MQA)
- ✅ Understand and implement rotary position embeddings (RoPE)
- ✅ Construct the complete transformer architecture
- ✅ Generate text from your model
- ✅ Implement different sampling strategies
- ✅ Debug shape and dimension issues in transformers
- ✅ Understand the data flow through an LLM

## 📅 Daily Breakdown

### Day 1.1: Attention and Multi-Head Attention
**Core Concepts**: Scaled dot product attention, multi-head attention mechanism
**Deliverable**: Working attention implementation

**Key Questions**:
- What problem does attention solve?
- How do Q, K, V matrices work together?
- Why do we need multiple heads?

**Implementation**: `code/week1/attention.py`

---

### Day 1.2: Positional Encodings and RoPE
**Core Concepts**: Positional embeddings, Rotary Position Embeddings
**Deliverable**: RoPE implementation integrated with attention

**Key Questions**:
- Why can't transformers understand position naturally?
- What's the difference between absolute and relative position encoding?
- How does RoPE work mathematically?

**Implementation**: `code/week1/rope.py`

---

### Day 1.3: Grouped/Multi Query Attention
**Core Concepts**: GQA, MQA, KV sharing across heads
**Deliverable**: Efficient attention variants

**Key Questions**:
- Why is standard MHA memory-intensive?
- What's the trade-off in GQA/MQA?
- When would you use each variant?

**Implementation**: `code/week1/gqa.py`

---

### Day 1.4: RMSNorm and MLP
**Core Concepts**: Root Mean Square Layer Normalization, Feed-Forward Networks
**Deliverable**: Normalization and MLP layers

**Key Questions**:
- Why normalize activations?
- What's the difference between RMSNorm and LayerNorm?
- What role does the MLP play in transformers?

**Implementation**: `code/week1/norm_mlp.py`

---

### Day 1.5: The Qwen2 Model
**Core Concepts**: Complete transformer architecture, decoder blocks
**Deliverable**: Full Qwen2 model implementation

**Key Questions**:
- How do all the components fit together?
- What's the data flow through the model?
- How does Qwen2 differ from other transformers?

**Implementation**: `code/week1/qwen2_model.py`

---

### Day 1.6: Generating the Response
**Core Concepts**: Autoregressive generation, token-by-token decoding
**Deliverable**: Text generation pipeline

**Key Questions**:
- How does autoregressive generation work?
- Why generate one token at a time?
- What's the relationship between prefill and decode?

**Implementation**: `code/week1/generation.py`

---

### Day 1.7: Sampling and Preparing for Week 2
**Core Concepts**: Temperature, top-p, top-k sampling
**Deliverable**: Multiple sampling strategies

**Key Questions**:
- How does temperature affect generation?
- What's the difference between greedy, top-k, and top-p?
- What are the trade-offs of each sampling method?

**Implementation**: `code/week1/sampling.py`

---

## 🛠️ Technical Stack

- **Primary**: MLX (Apple Silicon optimized)
- **Alternative**: PyTorch tensors (without high-level nn modules)
- **Language**: Python
- **Tools**: NumPy for matrix ops, basic Python libraries

## 📊 Week 1 Success Criteria

### Knowledge Checkpoints
- [ ] Can explain attention mechanism intuitively
- [ ] Can derive tensor shapes through the model
- [ ] Understands why each component exists
- [ ] Can debug shape/dimension errors
- [ ] Can trace data flow through complete model

### Implementation Checkpoints
- [ ] Attention produces correct output shapes
- [ ] RoPE correctly modifies Q and K
- [ ] GQA properly shares KV across head groups
- [ ] Complete model loads Qwen2 weights
- [ ] Model generates coherent text
- [ ] Multiple sampling strategies work

### Debugging Skills
- [ ] Can identify shape mismatch sources
- [ ] Can trace tensor transformations
- [ ] Can validate intermediate outputs
- [ ] Can compare with reference implementation

## 🎓 Study Strategy

### Daily Routine
1. **Morning** (1-2 hours):
   - Read course material thoroughly
   - Take notes on key concepts
   - Sketch out implementation approach

2. **Afternoon** (2-3 hours):
   - Implement the day's components
   - Test incrementally
   - Debug issues

3. **Evening** (1 hour):
   - Write session documentation
   - Review and refine code
   - Prepare questions for next day

### Weekly Workflow
- **Days 1-3**: Focus on understanding fundamentals deeply
- **Days 4-5**: Integrate components, see the big picture
- **Days 6-7**: End-to-end system, experimentation

## 💡 Tips for Success

1. **Start Simple**: Implement basic version first, then optimize
2. **Test Incrementally**: Validate each component before moving on
3. **Print Shapes**: Add shape prints everywhere while debugging
4. **Compare with Reference**: Use course reference to validate
5. **Ask Questions**: Use AI tutor (CLAUDE.md) with Socratic method
6. **Document as You Go**: Write session docs while memory is fresh
7. **Experiment**: Try breaking things to understand how they work

## 🚧 Common Pitfalls

- **Shape mismatches**: Most common error - track dimensions carefully
- **Broadcasting issues**: Understand how tensors broadcast
- **Forgetting to transpose**: K needs to be transposed in attention
- **Head dimension confusion**: Keep track of (batch, heads, seq, head_dim)
- **RoPE application**: Must apply to Q and K before attention
- **Residual connections**: Easy to forget to add them

## 📚 Key Resources

- **Course Website**: https://skyzh.github.io/tiny-llm
- **Week 1 Materials**: https://skyzh.github.io/tiny-llm/week1-overview.html
- **MLX Docs**: https://ml-explore.github.io/mlx/
- **Attention Paper**: "Attention is All You Need"
- **RoPE Paper**: "RoFormer: Enhanced Transformer with Rotary Position Embedding"

## 🔄 Connection to Week 2

Week 1 builds the foundation. Week 2 will optimize:
- **KV Cache**: Reuse previous computations
- **Quantization**: Reduce memory footprint
- **Flash Attention**: Memory-efficient attention
- **Batching**: Handle multiple requests

Understanding Week 1 deeply makes Week 2 optimizations clear.

---

**Ready to Start?** Begin with `sessions/week1/day1-attention.md`

**Course Link**: [Week 1 Overview](https://skyzh.github.io/tiny-llm/week1-overview.html)
