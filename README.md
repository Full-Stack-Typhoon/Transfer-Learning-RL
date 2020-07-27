# Comparing Transfer Learning in Humans and RL agents

## Abstract
Progressive Neural Networks (PNNs) are immune to catastrophic forgetting and can leverage prior knowledge via lateral connections to previously learned features (Rusu et al., 2016). We show that they also exhibit compositionality for previously learned concepts. We use PNNs to solve a series of Reinforcement Learning tasks and compare them with patterns of transfer learning in human cognition. Interestingly, we find that our networks exhibit characteristics of transfer that have also been demonstrated in human transfer learning tasks. Furthermore, when combined with a language component, our network1 can transfer previously learned concepts from the source task and compose them to solve the target task. **Paper.pdf** contains relevant examples of Positive Transfer, Negative transfer. 
## pytorch-a2c-ppo-acktr

## Please use hyper parameters from this readme. With other hyper parameters things might not work (it's RL after all)!

Original repository - [Link](https://github.com/ikostrikov/pytorch-a2c-ppo-acktr-gail)

This is a PyTorch implementation of
* Advantage Actor Critic (A2C), a synchronous deterministic version of [A3C](https://arxiv.org/pdf/1602.01783v1.pdf)
* Proximal Policy Optimization [PPO](https://arxiv.org/pdf/1707.06347.pdf)
* Scalable trust-region method for deep reinforcement learning using Kronecker-factored approximation [ACKTR](https://arxiv.org/abs/1708.05144)
* Generative Adversarial Imitation Learning [GAIL](https://arxiv.org/abs/1606.03476)



## Requirements

* Python 3 (it might work with Python 2, but I didn't test it)
* [PyTorch](http://pytorch.org/)
* [OpenAI baselines](https://github.com/openai/baselines)

In order to install requirements, follow:

```bash
# PyTorch
conda install pytorch torchvision -c soumith

# Baselines for Atari preprocessing
git clone https://github.com/openai/baselines.git
cd baselines
pip install -e .

# Other requirements
pip install -r requirements.txt
```


## Visualization

In order to visualize the results use ```visualize.ipynb```.


## Training

#### PPO Single column

```bash
python main.py --env-name "PongNoFrameskip-v4" --use-pnn --use-gae   --num-processes 8 --num-steps 128 --num-mini-batch 4  --use-linear-lr-decay 
```

#### Progressive neural network with 2 columns

```bash
python main.py --env-name "PongNoFrameskip-v4"  --use-pnn --n-columns 2 --pnn-paths "path_to_trained_model_from_previous_runs"  --use-gae   --num-processes 8 --num-steps 128 --num-mini-batch 4  --use-linear-lr-decay 
```

Works with minigrid environments. Pass 'MiniGrid-xyz' (change this to environment's name) as the argument for --env-name
