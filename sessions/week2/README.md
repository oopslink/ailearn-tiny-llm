# Week 2: Tiny vLLM

This week focuses on building efficient inference infrastructure and optimizations. You'll learn how to make your LLM fast, memory-efficient, and production-ready.

## 📚 Overview

**Duration**: 8+ days  
**Goal**: Implement serving optimizations for efficient inference  
**Approach**: Systems engineering - optimize compute, memory, and throughput

## 🎯 Learning Objectives

By the end of Week 2, you should be able to:

- ✅ Implement KV caching to avoid redundant computation
- ✅ Write custom C++/Metal kernels for quantized operations
- ✅ Implement Flash Attention for memory efficiency
- ✅ Build continuous batching for throughput optimization
- ✅ Understand compute vs. memory trade-offs
- ✅ Profile and optimize inference performance
- ✅ Debug low-level kernel code
- ✅ Implement chunked prefill for better batching

## 📅 Topics Breakdown

### Topic 2.1: Key-Value Cache
**Core Concepts**: Caching mechanism, autoregressive generation optimization
**Deliverable**: KV cache implementation

**Key Questions**:
- Why is naive generation inefficient?
- What gets cached and why?
- How does cache grow during generation?
- What are the memory implications?

**Implementation**: `code/week2/kv_cache.py`

**Performance Goal**: >10x speedup on generation

---

### Topics 2.2-2.3: Quantized Matrix Multiplication (2 days)
**Core Concepts**: Weight quantization, custom kernel programming
**Deliverable**: Quantized matmul kernels (CPU and GPU)

**Day 1: CPU Implementation**
- Integer quantization
- Dequantization during computation
- C++ kernel basics

**Day 2: GPU Implementation**
- Metal shader programming
- Memory coalescing
- Parallel reduction

**Key Questions**:
- What is quantization and why use it?
- What precision loss is acceptable?
- How do we optimize memory access patterns?
- What's the performance vs. accuracy trade-off?

**Implementation**: 
- `code/week2/quantize.py`
- `code/week2/kernels/matmul.cpp`
- `code/week2/kernels/matmul.metal`

**Performance Goal**: 2-4x memory reduction, <10% accuracy loss

---

### Topics 2.4-2.5: Flash Attention (2 days)
**Core Concepts**: Memory-efficient attention, tiling, online softmax
**Deliverable**: Flash attention implementation

**Day 1: Algorithm & CPU**
- Understand the Flash Attention paper
- Tiled attention computation
- Online softmax trick
- CPU implementation

**Day 2: GPU Optimization**
- Metal shader implementation
- Shared memory usage
- Block-wise computation

**Key Questions**:
- Why is standard attention memory-bound?
- How does tiling help?
- What is online softmax?
- When is Flash Attention beneficial?

**Implementation**:
- `code/week2/flash_attention.py`
- `code/week2/kernels/flash_attn.metal`

**Performance Goal**: O(N) memory instead of O(N²)

---

### Topics 2.6-2.7: Continuous Batching (2 days)
**Core Concepts**: Dynamic batching, request scheduling, throughput optimization
**Deliverable**: Continuous batching system

**Day 1: Theory & Design**
- Request lifecycle
- Scheduling algorithms
- Memory management
- Request state tracking

**Day 2: Implementation**
- Request queue management
- Dynamic batch formation
- Iteration-level scheduling
- Performance monitoring

**Key Questions**:
- Why batch requests together?
- How to handle varying sequence lengths?
- When to add/remove requests from batch?
- What are the scheduling trade-offs?

**Implementation**: `code/week2/continuous_batching.py`

**Performance Goal**: >5x throughput improvement

---

### Topic 2.8: Chunked Prefill
**Core Concepts**: Prefill/decode separation, chunking strategies
**Deliverable**: Chunked prefill implementation

**Key Questions**:
- What's the difference between prefill and decode?
- Why chunk the prefill phase?
- How to balance prefill vs. decode in a batch?

**Implementation**: `code/week2/chunked_prefill.py`

**Performance Goal**: Better latency for decode requests

---

## 🛠️ Technical Stack

- **MLX**: Core ML operations
- **C++**: Custom CPU kernels
- **Metal**: Apple Silicon GPU kernels
- **CMake**: Build system for C++ components
- **Python/C++ bindings**: pybind11 or ctypes

## 📊 Week 2 Success Criteria

### Knowledge Checkpoints
- [ ] Understands caching strategies
- [ ] Can explain quantization trade-offs
- [ ] Knows Flash Attention algorithm
- [ ] Understands batching strategies
- [ ] Can reason about memory/compute trade-offs

### Implementation Checkpoints
- [ ] KV cache reduces generation time
- [ ] Quantized kernels compile and run
- [ ] Flash Attention produces correct output
- [ ] Continuous batching handles multiple requests
- [ ] Chunked prefill integrates with batching

### Systems Skills
- [ ] Can profile Python/C++ code
- [ ] Can debug kernel code
- [ ] Can measure memory usage
- [ ] Can optimize for throughput vs. latency
- [ ] Can validate numerical accuracy

## 🎓 Study Strategy

### Learning Approach
1. **Understand the problem** before implementing solution
2. **Start with simple version** (Python), then optimize (C++/Metal)
3. **Measure everything** - profile before and after
4. **Validate correctness** - compare with reference implementation
5. **Iterate on performance** - optimize hot paths

### Daily Routine
1. **Theory** (1-2 hours): Understand the optimization
2. **Prototype** (2-3 hours): Implement in Python
3. **Optimize** (2-3 hours): Write custom kernels
4. **Validate** (1 hour): Test correctness and performance
5. **Document** (1 hour): Write session notes

## 💡 Tips for Success

1. **Profile First**: Measure where time is spent before optimizing
2. **Correctness Before Speed**: Get it working, then make it fast
3. **Small Tests**: Debug with tiny inputs first
4. **Compare Outputs**: Validate against reference implementation
5. **Memory Matters**: Track allocations carefully
6. **Learn from Reference**: Study vLLM and other inference engines
7. **Ask "Why"**: Understand the motivation for each optimization

## 🚧 Common Pitfalls

### KV Cache
- **Memory leaks**: Forgetting to clear old cache entries
- **Shape errors**: Cache shapes with batching
- **Position tracking**: Maintaining correct positions

### Quantization
- **Numerical issues**: Integer overflow, rounding errors
- **Calibration**: Choosing good quantization scales
- **Kernel bugs**: Off-by-one errors, race conditions

### Flash Attention
- **Tiling logic**: Getting block sizes right
- **Online softmax**: Numerical stability issues
- **Memory management**: Shared memory usage

### Continuous Batching
- **Scheduling complexity**: Request ordering logic
- **Memory fragmentation**: Efficient memory reuse
- **State management**: Tracking request states

## 🔍 Debugging Tools

- **Python profilers**: cProfile, line_profiler
- **Memory profilers**: memory_profiler, tracemalloc
- **MLX profiling**: Built-in profiling tools
- **Print debugging**: Shape and value inspection
- **Unit tests**: Isolated component testing
- **Numerical validation**: Compare with reference

## 📚 Key Resources

### Papers
- **Flash Attention**: "FlashAttention: Fast and Memory-Efficient Exact Attention"
- **vLLM**: "Efficient Memory Management for Large Language Model Serving"
- **Quantization**: "LLM.int8(): 8-bit Matrix Multiplication for Transformers"

### Documentation
- **MLX**: https://ml-explore.github.io/mlx/
- **Metal**: Apple Metal Shading Language
- **C++**: Modern C++ for kernel programming

### Reference Implementations
- **vLLM**: https://github.com/vllm-project/vllm
- **llama.cpp**: https://github.com/ggerganov/llama.cpp
- **Text Generation Inference**: https://github.com/huggingface/text-generation-inference

## 🔗 Connection to Week 1

Week 1 gave you the **what** - a working LLM.  
Week 2 teaches the **how** - making it production-ready.

### Building on Week 1
- **Attention** → Flash Attention (memory optimization)
- **Generation** → KV Cache (compute optimization)
- **Single request** → Continuous Batching (throughput optimization)
- **Full precision** → Quantization (memory optimization)

## 🎯 Performance Targets

By end of Week 2, compared to naive Week 1 implementation:

| Optimization | Target Improvement |
|--------------|-------------------|
| KV Cache | 10x+ faster generation |
| Quantization | 2-4x memory reduction |
| Flash Attention | 2-3x faster attention |
| Continuous Batching | 5x+ throughput |
| **Combined** | **50x+ throughput improvement** |

## 🔄 Connection to Week 3

Week 2 builds the core serving infrastructure.  
Week 3 adds advanced production features:
- **Paged Attention**: Even better memory management
- **Speculative Decoding**: Faster generation
- **MoE**: Efficient large models
- **RAG/Tools**: Practical applications

---

**Ready to Start?** Begin with `sessions/week2/topic1-kv-cache.md`

**Course Link**: [Week 2 Overview](https://skyzh.github.io/tiny-llm/week2-overview.html)
