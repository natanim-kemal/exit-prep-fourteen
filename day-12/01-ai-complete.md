# Artificial Intelligence — Study Notes

## 1. AI Fundamentals

**AI (Artificial Intelligence)**: machines performing tasks that require human intelligence (reasoning, learning, perception, problem-solving). AI is a rapidly evolving field requiring continuous learning to stay updated.

**Branches of AI**:
- **Machine Learning**: algorithms that improve through experience/data
- **Deep Learning**: neural networks with many layers
- **Natural Language Processing (NLP)**: understanding/ generating human language
- **Computer Vision**: interpreting visual information
- **Robotics**: intelligent agents in physical world
- **Expert Systems**: rule-based knowledge representation

## 2. Intelligent Agents

An agent perceives its environment through sensors and acts through actuators.

**Types by capability**:
- **Simple Reflex Agent**: responds to current percept only; no memory
- **Model-based Agent**: maintains internal model of the world updated by percepts
- **Goal-based Agent**: acts to achieve goals; can plan ahead
- **Utility-based Agent**: maximizes a utility function (preference-based)
- **Learning Agent**: improves performance over time through experience

## 3. Problem-Solving & Search

**Search algorithms**:
- **Uninformed**: BFS, DFS, Uniform Cost Search — no domain knowledge
- **Informed**: A*, Greedy Best-First — use heuristic function

**State space representation**: states, actions, transition model, goal test, path cost.

**Heuristic function**: estimate of cost from current state to goal. Admissible (never overestimates) for optimal A*.

## 4. Knowledge Representation

**Methods**:
- **Logical representation**: formal logic (propositional, first-order) — precise but complex
- **Semantic network**: graph of concepts and relationships (IS-A, HAS-A)
- **Frame representation**: structured object with slots/attributes
- **Rule-based**: IF-THEN rules (expert systems)
- **Production rules**: condition-action pairs

**Frame example**: Representing "Samuel is a player, age 25, height 1.98, club Manchester, lives in England" as a frame with slots (Name, Age, Height, Club, Residence).

## 5. Natural Language Processing (NLP)

**Key tasks**:
- **Tokenization**: breaking text into words/tokens
- **POS Tagging**: identifying parts of speech
- **Named Entity Recognition (NER)**: identifying names, places, dates
- **Sentiment Analysis**: determining emotional tone
- **Machine Translation**: translating between languages

**TF-IDF (Term Frequency-Inverse Document Frequency)**: measures term importance in a document relative to a corpus.

## 6. Expert Systems

Components:
- **Knowledge Base**: domain facts and rules
- **Inference Engine**: applies rules to facts (Forward/Backward chaining)
- **User Interface**: interaction with user
- **Explanation Module**: explains reasoning

**Limitations**: knowledge acquisition bottleneck, lack of common sense, brittle (cannot handle novel situations well).

## 7. AI Ethics & Challenges

- **Bias**: AI systems can perpetuate/amplify biases in training data
- **Transparency**: "black box" problem — difficult to explain decisions
- **Privacy**: data collection and usage concerns
- **Safety**: ensuring AI systems behave as intended
- **Job displacement**: automation affecting employment

**Turing Test**: test of machine's ability to exhibit intelligent behavior indistinguishable from a human.

## 8. Key Differences

**AI vs ML vs Deep Learning**: AI is the broadest (machines mimicking human intelligence). ML is a subset (learning from data). Deep Learning is a subset of ML (neural networks).
