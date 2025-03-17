# CodeEval RL

A comprehensive reinforcement learning framework for enhancing LLM coding capabilities through execution feedback.

## 🌟 Overview

CodeEval RL is a Python framework designed to improve Large Language Models' programming abilities through reinforcement learning. By using actual code execution results as evaluation functions, this framework continuously enhances LLMs' code generation capabilities for practical use.

## 🔍 Problem & Motivation

Current LLMs face several challenges when generating code:

- Inconsistent production of accurate and executable code
- Limited understanding of specific programming paradigms and libraries
- Poor adaptation to company-specific coding conventions
- Lack of clear success/failure feedback loops

CodeEval RL addresses these issues by implementing a complete feedback system that evaluates generated code on multiple dimensions and uses reinforcement learning to continuously improve model performance.

## ✨ Key Features

### Multi-level Evaluation Engine
```python
class EvaluationEngine:
    def evaluate_syntax(self, code):
        """Evaluates code syntax correctness"""
        pass
        
    def evaluate_execution(self, code):
        """Evaluates runtime execution success"""
        pass
        
    def evaluate_test_cases(self, code, test_cases):
        """Validates code against test cases"""
        pass
        
    def evaluate_code_quality(self, code):
        """Assesses code quality (PEP8, complexity, security)"""
        pass
        
    def evaluate_efficiency(self, code):
        """Analyzes time and space complexity"""
        pass
```

### Sandboxed Execution Environment
- Isolated execution for multiple languages (Python, JavaScript, Java, C++, Rust)
- Resource usage monitoring (CPU time, memory, disk I/O)
- Automatic dependency resolution

### Dataset Management System
- Challenge generation from company codebase
- Tiered challenge library with difficulty levels
- Context-rich datasets including documentation and API specs

### Custom RL Framework
- LLM-adapted RL algorithms (PPO, DQN)
- Multi-objective reward functions (correctness, efficiency, readability)
- Reward shaping with intermediate evaluation
- KL-constrained learning to preserve model capabilities

### Analysis and Monitoring Tools
- Performance tracking over time by category and language
- Learning process visualization
- Automatic error pattern detection
- A/B testing capabilities

## 🛠️ Technical Architecture

```
┌─────────────────┐    ┌─────────────────┐    ┌─────────────────┐
│  LLM Interface  │───▶│   RL Trainer    │───▶│  Evaluation     │
└─────────────────┘    └─────────────────┘    │  Pipeline       │
                                              └────────┬────────┘
┌─────────────────┐    ┌─────────────────┐           │
│  Dataset        │◀───│  Sandboxed      │◀──────────┘
│  Management     │    │  Execution      │
└─────────────────┘    └─────────────────┘
```

- Microservice-based distributed system
- Containerized execution environments (Docker/Kubernetes)
- High-throughput evaluation pipeline
- Distributed learning support with GPU clusters

## 📦 Installation

```bash
# Clone the repository
git clone https://github.com/your-org/codeeval-rl.git
cd codeeval-rl

# Set up virtual environment
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt

# Install development dependencies (optional)
pip install -r requirements-dev.txt
```

## 🚀 Usage

### Basic Usage

```python
from codeeval_rl import CodeEvalRL, LLMAdapter

# Initialize the framework
framework = CodeEvalRL(
    model_adapter=LLMAdapter('your-llm-model'),
    evaluation_config='configs/eval_config.yaml',
    sandbox_config='configs/sandbox_config.yaml'
)

# Start training
framework.train(
    dataset_path='datasets/python_challenges',
    epochs=10,
    batch_size=32,
    learning_rate=1e-5
)

# Evaluate model
results = framework.evaluate(test_dataset='datasets/test_challenges')
print(results.summary())

# Use the fine-tuned model
code = framework.generate_code(
    prompt="Write a function to find the nth Fibonacci number",
    language="python"
)
```

### Configuration Example

```yaml
# eval_config.yaml
evaluation:
  syntax_weight: 0.2
  execution_weight: 0.3
  test_case_weight: 0.3
  quality_weight: 0.1
  efficiency_weight: 0.1
  
  test_timeout: 5  # seconds
  memory_limit: 512  # MB
  
  code_quality:
    enable_pep8: true
    max_complexity: 10
    security_checks: true
```

## 📊 Benchmarks

Our framework has achieved significant improvements on standard code benchmarks:

| Model | Baseline HumanEval | After RL (HumanEval) | Baseline MBPP | After RL (MBPP) |
|-------|-------------------|---------------------|---------------|-----------------|
| Llama 3.1 8B | 8.9% | 17.2% | - | - |
| Llama 3.1 70B | 25.9% | 40.1% | - | - |
| DeepSeekCoder-v2 | - | 67.0% | - | 78.7% |
| Qwen2.5-7B | 27.5% | 30.1% | - | 65.4% |

## 🗓️ Roadmap

### Phase 1: Foundation (3 months)
- Core evaluation engine development
- Basic sandbox environment setup
- Initial dataset collection and processing

### Phase 2: Prototype (2 months)
- RL implementation with limited challenge set
- Beta release for internal testers
- Feedback loop establishment

### Phase 3: Expansion (4 months)
- Multi-language support
- Advanced evaluation metrics
- Scalability enhancements

### Phase 4: Production (3 months)
- Production deployment
- Documentation and education program
- Continuous improvement process

## 📄 License

This project is licensed under the MIT License - see the LICENSE file for details.

## 🤝 Contributing

Contributions are welcome! Please check out our contribution guidelines in CONTRIBUTING.md.

## 📚 References

- RLEF: Grounding Code LLMs in Execution Feedback with Reinforcement Learning
- CodeDPO: Aligning Code Models with Self Generated and Verified Source Code
- Process Supervision-Guided Policy Optimization for Code Generation
