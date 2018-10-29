# BipedalWalker-v2

BipedalWalker-v2 defines "solving" as getting average reward of 300 over 100 consecutive trials
Reward is given for moving forward, total 300+ points up to the far end. If the robot falls, it gets -100. Applying motor torque costs a small amount of points, more optimal agent will get better score. State consists of hull angle speed, angular velocity, horizontal speed, vertical speed, position of joints and joints angular speed, legs contact with ground, and 10 lidar rangefinder measurements. There's no coordinates in the state vector.

### A3C LSTM

![A3C LSTM playing BipedalWalker-v2](https://github.com/ksajan/BipedalWalker-v2/blob/master/Demo/BipedalWalker.gif)

This repo represents implementation with reinforcement learning using Asynchronous Advantage Actor-Critic (A3C) in Pytorch an algorithm from Google Deep Mind's paper "Asynchronous Methods for Deep Reinforcement Learning." on BipedalWalker-v2.

## Requirements

- Python 3.6+
- Openai Gym ( refere to [gym](https://github.com/openai/gym)
- Pytorch(depending upon your system without GPU - conda install pytorch-cpu torchvision-cpu -c pytorch)
- setproctitle(pip install setproctitle)

## Algorithm: Asynchronous Advantage Actor-Critic

### Define Parameters

lr: 0.0001 : Number of steps in training loop
gamma: 0.99 : Number by how much to check model 
tau: 1.0 :Number by increasing training steps
seed: 1 : Random Seed for generating noice
workers: 6 : Assigned cores for trainning the model
num_steps: 20 : Number of steps to be taken
max_episode_length: 10000 : Mac number of steps per episode
env: BipedalWalker-v2 : enviroment
optimizer: Adam : Optimization using adam activation function
model: MLP : model used for traing enviroment
stack_frames: 1 : Per grame to be stacked in training
gpu_ids: [-1] : Ids assigned to use gpu
  
 ## Training
 
 While training this model please make sure you assign the worker efficiently other wise it will not take forever to train.
 *To train this model with 6 worker(core) on my Predator 300 helios took 3 hours to result in some good rewards.
```
python main.py --workers 6 --env BipedalWalker-v2 --save-max True --model MLP --stack-frames 1
```
## Evaluation

To run a 100 episode gym evaluation with trained model
```
python gym_eval.py --env BipedalWalkerHardcore-v2 --num-episodes 100 --stack-frames 1 --model CONV --new-gym-eval True
```

## Project Reference

- https://github.com/ikostrikov/pytorch-a3c
- https://github.com/andrewliao11/pytorch-a3c-mujoco
- https://github.com/dgriff777/a3c_continuous
- https://github.com/liampetti/A3C-LSTM


## References

[Asynchronous Methods for Deep Reinforcement Learning][1]

[Konda, V. R., & Tsitsiklis, J. N. (2000). Actor-Critic Algorithms. Nips.][2]

[Asynchronous Advantage ActorCritic with Adam Optimization and a Layer Normalized Recurrent Network JOAKIM BERGDAHL][3]

[Vision Enhanced Asynchronous Advantage Actor-Critic on Racing Games][4]

[Mnih, V., Silver, D., & Riedmiller, M. (2013). Playing Atari with Deep Reinforcement Learning, 1–9.][5]

[Salimans, T., Ho, J., Chen, X., & Sutskever, I. (2017). Evolution Strategies as a Scalable Alternative to Reinforcement Learning, 1–13.][6]

[Deep Reinforcement Learning using Memory-based Approaches][7]

[Simple Reinforcement Learning with Tensorflow Part 8: Asynchronous Actor-Critic Agents (A3C)][8]

<!-- Links -->

[1]: https://arxiv.org/pdf/1602.01783.pdf
[2]: http://web.mit.edu/jnt/www/Papers/J094-03-kon-actors.pdf
[3]: https://pdfs.semanticscholar.org/06e2/afbb05ee7f7c7a04de2869ca417155f9f5ae.pdf
[4]: http://cs231n.stanford.edu/reports/2017/pdfs/617.pdf
[5]: https://www.cs.toronto.edu/~vmnih/docs/dqn.pdf
[6]: https://arxiv.org/pdf/1703.03864.pdf
[7]: http://cs231n.stanford.edu/reports/2017/pdfs/618.pdf
[8]: https://medium.com/emergent-future/simple-reinforcement-learning-with-tensorflow-part-8-asynchronous-actor-critic-agents-a3c-c88f72a5e9f2


#### Note
- I will update the files as it progress Right now facing difficulty n training model BipedalWalker-v2 on gpu and on cpu its taling lot of time as of now the model passes the reward thresold value but can't keep it up it varies a lot with margin of 200 - -200 as of now.
