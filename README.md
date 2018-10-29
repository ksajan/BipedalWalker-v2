# BipedalWalker-v2
### A3C LSTM

![A3C LSTM playing BipedalWalker-v2](https://github.com/ksajan/BipedalWalker-v2/blob/master/Demo/BipedalWalker.gif)

This repo represents implementation with reinforcement learning using Asynchronous Advantage Actor-Critic (A3C) in Pytorch an algorithm from Google Deep Mind's paper "Asynchronous Methods for Deep Reinforcement Learning." on BipedalWalker-v2.

### Requirements

- Python 3.6+
- Openai Gym ( refere to [gym](https://github.com/openai/gym)
- Pytorch(depending upon your system without GPU - conda install pytorch-cpu torchvision-cpu -c pytorch)
- setproctitle(pip install setproctitle)
 
 
 ## Training
 
 While training this model please make sure you assign the worker efficiently other wise it will not take forever to train.
 *To train this model with 6 worker(core) on my Predator 300 helios took 3 hours to result in some good rewards.
```
python main.py --workers 6 --env BipedalWalker-v2 --save-max True --model MLP --stack-frames 1
```
## Evaluation

To run a 100 episode gym evaluation with trained model
```
python gym_eval.py --env BipedalWalkerHardcore-v2 --num-episodes 100 --stack-frames 4 --model CONV --new-gym-eval True
```

## Project Reference

- https://github.com/ikostrikov/pytorch-a3c
- https://github.com/andrewliao11/pytorch-a3c-mujoco
- https://github.com/dgriff777/a3c_continuous
