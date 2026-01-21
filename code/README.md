# Code Implementation

This directory contains all code implementations for the tiny-llm learning project, organized by week.

## 📁 Structure

```
code/
├── week1/          # Week 1: From Matmul to Text
├── week2/          # Week 2: Tiny vLLM optimizations
└── week3/          # Week 3: Advanced serving features
```

## 🎯 Implementation Guidelines

### Code Style
- **Clarity over cleverness**: Write pedagogical code that's easy to understand
- **Document shapes**: Add comments showing tensor shapes
- **Type hints**: Use type annotations for function signatures
- **Docstrings**: Explain what each function does and why

### Testing
- Write tests for each component
- Validate against reference implementations
- Test edge cases (batch_size=1, empty inputs, etc.)
- Use assertions for shape validation

### Performance
- Profile before optimizing
- Document performance characteristics
- Compare with reference implementations
- Track memory usage

## 📝 Documentation Standards

### Function Documentation
```python
def scaled_dot_product_attention(q, k, v, mask=None):
    """
    Compute scaled dot product attention.
    
    Args:
        q: Query tensor of shape (batch, heads, seq_q, head_dim)
        k: Key tensor of shape (batch, heads, seq_k, head_dim)
        v: Value tensor of shape (batch, heads, seq_k, head_dim)
        mask: Optional mask of shape (batch, 1, seq_q, seq_k)
    
    Returns:
        attention_output: Shape (batch, heads, seq_q, head_dim)
        
    Mathematical formulation:
        Attention(Q, K, V) = softmax(Q @ K^T / sqrt(d_k)) @ V
    """
    # Implementation with shape comments
    pass
```

### Shape Comments
```python
# q: (batch=2, heads=8, seq=128, head_dim=64)
# k: (batch=2, heads=8, seq=128, head_dim=64)
# scores: (batch=2, heads=8, seq=128, seq=128)
scores = q @ k.transpose(-2, -1) / math.sqrt(head_dim)
```

## 🧪 Testing Approach

### Unit Tests
Test individual components in isolation:
```python
def test_attention_shapes():
    """Test that attention produces correct output shapes."""
    q = mx.random.normal((2, 8, 128, 64))
    k = mx.random.normal((2, 8, 128, 64))
    v = mx.random.normal((2, 8, 128, 64))
    
    output = scaled_dot_product_attention(q, k, v)
    assert output.shape == (2, 8, 128, 64)
```

### Integration Tests
Test components working together:
```python
def test_qwen2_forward():
    """Test complete model forward pass."""
    model = Qwen2Model(config)
    input_ids = mx.array([[1, 2, 3, 4]])
    output = model(input_ids)
    # Validate output shape and properties
```

### Validation Tests
Compare with reference implementations:
```python
def test_attention_correctness():
    """Compare our attention with reference implementation."""
    # Create same inputs
    # Run both implementations
    # Assert outputs are close (within tolerance)
```

## 📊 Performance Tracking

Document performance for key components:
```python
"""
Performance characteristics:
- Forward pass: ~10ms for seq_len=128
- Memory: ~2GB for Qwen2-0.5B
- Attention: O(n²) complexity, memory-bound

Optimizations applied:
- None yet (baseline implementation)

Week 2 targets:
- KV cache: 10x faster generation
- Flash attention: 3x faster, O(n) memory
"""
```

## 🚀 Week-by-Week Guide

### Week 1: Focus on Correctness
- Implement each component carefully
- Validate shapes at every step
- Test thoroughly before moving on
- Compare with reference when possible
- Don't optimize prematurely

### Week 2: Focus on Performance
- Profile to find bottlenecks
- Implement optimizations incrementally
- Measure improvement after each change
- Balance speed vs. accuracy
- Write efficient kernels

### Week 3: Focus on Integration
- Combine optimizations
- Handle edge cases
- Add error handling
- Build complete systems
- Think about production use

## 💡 Development Workflow

1. **Read course material** - Understand concept first
2. **Design API** - Think about interfaces
3. **Implement simple version** - Get it working
4. **Add tests** - Validate correctness
5. **Compare with reference** - Check accuracy
6. **Document** - Add docstrings and comments
7. **Optimize (Week 2+)** - Improve performance
8. **Integrate** - Connect with other components

## 🐛 Debugging Tips

### Shape Errors
```python
# Add shape prints everywhere during development
print(f"q shape: {q.shape}")
print(f"k shape: {k.shape}")
print(f"scores shape: {scores.shape}")
```

### Numerical Issues
```python
# Check for NaN/Inf
assert not mx.any(mx.isnan(output)), "NaN detected!"
assert not mx.any(mx.isinf(output)), "Inf detected!"

# Check value ranges
print(f"Output range: [{output.min()}, {output.max()}]")
```

### Performance Issues
```python
import time

start = time.time()
output = model(input_ids)
print(f"Forward pass: {time.time() - start:.3f}s")
```

## 📚 Useful Patterns

### Shape Assertions
```python
def forward(self, x):
    batch, seq, dim = x.shape
    assert dim == self.hidden_dim, f"Expected dim={self.hidden_dim}, got {dim}"
    # Rest of implementation
```

### Lazy Initialization
```python
class Model:
    def __init__(self, config):
        self.config = config
        # Lazy init - create layers on first forward pass
        self.layers = None
    
    def _init_layers(self):
        if self.layers is None:
            self.layers = [Layer(self.config) for _ in range(self.config.n_layers)]
```

### Shape Transformation Helpers
```python
def reshape_for_heads(x, n_heads):
    """Reshape (batch, seq, dim) -> (batch, heads, seq, head_dim)"""
    batch, seq, dim = x.shape
    head_dim = dim // n_heads
    return x.reshape(batch, seq, n_heads, head_dim).transpose(0, 2, 1, 3)
```

## 🔗 Resources

- **MLX Examples**: https://github.com/ml-explore/mlx-examples
- **Reference Implementations**: Check course repo
- **Debugging**: Use MLX's built-in profiling tools

---

**Remember**: The goal is **learning**, not building production code. Prioritize understanding over optimization (until Week 2!).
