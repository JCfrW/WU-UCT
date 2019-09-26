# P-UCT
A novel parallel UCT algorithm with linear speedup and negligible performance loss. This package provide demo on Atari games (see [Run on your own environments](#Run-on-your-own-environments)） To allow easy extension to other environments, we include an environment [wrapper file](./Env/EnvWrapper.py)

# Introduction
Note: For full details of P-UCT, please refer to our [Arxiv](https://arxiv.org) paper.

# Usage
## Prerequisites
- Python 3.x
- PyTorch 1.0
- Gym (with atari) 0.14.0
- Numpy 1.17.2
- Scipy 1.3.1
- OpenCV-Python 4.1.1.26

## Running
1. Download or clone the repository.
2. Run with the default settings:
```
  python3 main.py --model P-UCT
```
3. For additional hyperparameters please have a look at [main.py](./main.py), where descriptions are also included. For example, if you want to run the game PongNoFrameskip-v0 with 200 MCTS rollouts, simply run:
```
  python3 main.py --model P-UCT --env-name PongNoFrameskip-v0 --MCTS-max-steps 200
```

### Planning with prior policy
The code currently support three default policies (policy used to perform simulation): *Random*, *PPO*, *DistillPPO* (to use them, change the “--policy” parameter). To use the *PPO* and *DistillPPO* policy, corresponding policy files need to be put in [./Policy/PPO/PolicyFiles](./Policy/PPO/PolicyFiles). PPO policy files can be generated by [Atari_PPO_training](./Utils/Atari_PPO_training). For example, by running
```
  cd Utils/Atari_PPO_training
  python3 main.py PongNoFrameskip-v0
```
a policy file will be generated in [./Utils/Atari_PPO_training/save](./Utils/Atari_PPO_training/save). To run DistillPPO, we have to run the distill training process by
```
  python3 main.py --mode Distill --env-name PongNoFrameskip-v0
```

## Run on your own environments
We kindly provide an [environment wrapper](./Env/EnvWrapper.py) to make easy extensions to other environments. All you need is to modify [./Env/EnvWrapper.py](./Env/EnvWrapper.py) and fit in your own environment. Specifically, you just need to rewrite APIs in the EnvWrapper class.

# Reference
Please cite the paper in the following format if you used this code during your research :)
```
@inproceedings{
anonymous2020watch,
title={Watch the Unobserved: A Simple Approach to Parallelizing Monte Carlo Tree Search},
author={Anonymous},
booktitle={Submitted to International Conference on Learning Representations},
year={2020},
url={https://openreview.net/forum?id=BJlQtJSKDB},
note={under review}
}
```
