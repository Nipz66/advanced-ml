# Week 01 – Introduction to ML

## Key concepts

- What is intelligence
- What is artificial intelligence
- Deterministic vs probabilistic relationships
- What is machine learning
- ML subdomains
- Artificial neural networks (3 or more hidden layers = deep learning)

## What I learnt

### 1. What is intelligence

Intelligence is the ability to learn from experience, understand information, reason about it, and use that knowledge to solve problems or make decisions. In humans it covers things like learning, memory, reasoning, and adapting to new situations.

### 2. What is artificial intelligence (AI)

Artificial intelligence is the field of building machines or software that can perform tasks which normally require human intelligence — for example understanding language, recognising images, making decisions, or solving problems. The goal is to make machines *imitate* the way humans think and act.

### 3. Deterministic vs probabilistic relationships

- **Deterministic relationship:** For a given input, the output is always exactly the same. There is no uncertainty. Example: area of a circle = π × r². The same radius always gives the same area.
- **Probabilistic relationship:** The output involves uncertainty, so instead of one fixed answer we talk about the *likelihood* of an outcome. Example: predicting whether it will rain tomorrow — the same conditions might give an 80% chance of rain, not a guaranteed yes/no.

Machine learning mostly deals with probabilistic relationships, because real-world data has noise and uncertainty.

### 4. What is machine learning (ML)

Machine learning is a subdomain of AI where the system **learns patterns directly from data** instead of being given explicit step-by-step rules. You show the model many examples, it finds the patterns, and then it can make predictions on new, unseen data.

- Traditional programming: Rules + Data → Answers
- Machine learning: Data + Answers → Rules (the model learns the rules)

### 5. ML subdomains

The main types of machine learning are:

- **Supervised learning:** Learns from labelled data (input + correct answer). Used for prediction and classification. Example: spam vs not-spam email.
- **Unsupervised learning:** Learns from unlabelled data by finding hidden patterns or groups. Example: customer segmentation.
- **Reinforcement learning:** Learns by trial and error through rewards and penalties. Example: a game-playing agent or a robot learning to walk.

### 6. Artificial neural networks (ANN)

An artificial neural network is a model inspired by the human brain. It is made of connected units called **neurons**, arranged in layers:

- **Input layer** – receives the data
- **Hidden layer(s)** – process the data and learn patterns
- **Output layer** – gives the final result

**Deep learning:** When a neural network has **3 or more hidden layers**, it is called deep learning. More hidden layers let the network learn more complex patterns.