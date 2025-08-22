# Deep Q-Learning for Frozen Lake and Cliff Walking Environments

This repository contains implementations of various reinforcement learning algorithms applied to classic Gymnasium environments: Frozen Lake and Cliff Walking. The project was developed as part of an Advanced Deep Learning assignment and executed on Google Colab.

## Project Overview

The project explores different reinforcement learning approaches:
1. **Q-Learning** - Traditional tabular Q-learning
2. **Deep Q-Learning** - Neural network-based Q-learning with experience replay
3. **Deep Q-Learning with Policy and Target Networks** - Enhanced DQN with target network for stability

## Environments

### Frozen Lake Environment
- **Map**: 3x3 grid with Start (S), Frozen (F), Hole (H), and Goal (G)
- **Objective**: Navigate from start to goal without falling into holes
- **Actions**: 4 directions (left, down, right, up)
- **Rewards**: 0 for each step, 1 for reaching goal, 0 for falling into hole

### Cliff Walking Environment
- **Map**: 4x12 grid with cliff edges
- **Objective**: Navigate from start to goal while avoiding cliff edges
- **Actions**: 4 directions (up, right, down, left)
- **Rewards**: -1 for each step, -100 for falling off cliff, -1 for reaching goal

## Implementation Results

### 1. Q-Learning (Frozen Lake)
- **Success Rate**: 100.00%
- **Training Episodes**: 1000
- **Optimal Path**: [2, 2, 1, 1, 1, 2] (6 steps)
- **Key Finding**: Achieved perfect success rate with fast convergence

### 2. Deep Q-Learning (Frozen Lake)
- **Training Episodes**: 500
- **Network Architecture**: 3-layer neural network (9 → 24 → 24 → 4)
- **Hyperparameters**: 
  - Learning rate: 0.001
  - Epsilon decay: 0.003
  - Discount factor: 0.9
  - Batch size: 256
- **Test Result**: Successfully reached goal in 4 steps
- **Optimal Policy**: Generated for all 9 states

### 3. Deep Q-Learning with Policy and Target Networks (Frozen Lake)
- **Training Episodes**: 700
- **Network Architecture**: Separate policy and target networks
- **Target Network Update**: Every 8 steps
- **Test Result**: Successfully reached goal in 4 steps
- **Comparison**: Slightly delayed learning but improved stability

### 4. Deep Q-Learning (Cliff Walking)
- **Training Episodes**: 1000
- **Network Architecture**: Enhanced with dropout layers
- **Hyperparameters**:
  - Learning rate: 0.001
  - Epsilon decay: 0.001
  - Discount factor: 0.9
  - Batch size: 512
- **Test Result**: Successfully navigated to goal in 13 steps
- **Optimal Policy**: Generated for all 48 states

## Key Findings

### Performance Comparison
1. **Q-Learning vs Deep Q-Learning**: Q-Learning achieved higher success rate (100% vs ~80%) and faster training for the simple 3x3 Frozen Lake environment
2. **Single vs Dual Networks**: Policy + Target network approach showed improved stability but slightly delayed learning
3. **Environment Complexity**: Deep Q-Learning performed well on the more complex Cliff Walking environment

### Technical Insights
- **Experience Replay**: Critical for stable training in Deep Q-Learning
- **Epsilon Decay**: Proper exploration-exploitation balance essential
- **Target Networks**: Improved convergence stability in complex environments
- **Network Architecture**: Dropout layers helped prevent overfitting in larger environments

## Files Structure

- `QLearning-frozen-walk.ipynb` - Traditional Q-Learning implementation
- `deep-QLearning-frozen-walk.ipynb` - Deep Q-Learning with single network
- `deep-QLearning-policy-target-network-frozen-walk.ipynb` - Deep Q-Learning with policy and target networks
- `deep-QLearning-cliff-walking.ipynb` - Deep Q-Learning applied to Cliff Walking environment

## Dependencies

- gymnasium[toy-text]
- tensorflow/keras
- numpy
- matplotlib
- imageio
- pandas

## Execution

All notebooks were executed on Google Colab with the following setup:
- Python 3.8/3.10
- GPU runtime (when available)
- Automatic dependency installation via pip

## Results Summary

| Method | Environment | Success Rate | Steps to Goal | Training Episodes |
|--------|-------------|--------------|---------------|-------------------|
| Q-Learning | Frozen Lake | 100% | 6 | 1000 |
| Deep Q-Learning | Frozen Lake | ~80% | 4 | 500 |
| DQN + Target Network | Frozen Lake | ~80% | 4 | 700 |
| Deep Q-Learning | Cliff Walking | Success | 13 | 1000 |

The project demonstrates the effectiveness of different reinforcement learning approaches across varying environment complexities, with each method showing strengths in different scenarios.
