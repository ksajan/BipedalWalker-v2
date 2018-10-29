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


## References

[Ioffe, S., & Szegedy, C. (2015). Batch Normalization: Accelerating Deep Network Training by Reducing Internal Covariate Shift. Arxiv, 1–11.][1]

[Konda, V. R., & Tsitsiklis, J. N. (2000). Actor-Critic Algorithms. Nips.][2]

[Lillicrap, T. P., Hunt, J. J., Pritzel, A., Hess, N., Erez, T., Tassa, Y., … Wierstra, D. (2016). Continuous control with deep reinforcement learning. Foundations and Trends® in Machine Learning, 2][3]

[Mnih, V. et al. (2015). Human-level control through deep reinforcement learning. Nature.][4]

[Mnih, V., Silver, D., & Riedmiller, M. (2013). Playing Atari with Deep Reinforcement Learning, 1–9.][5]

[Salimans, T., Ho, J., Chen, X., & Sutskever, I. (2017). Evolution Strategies as a Scalable Alternative to Reinforcement Learning, 1–13.][6]

[Silver, D., Lever, G., Heess, N., Degris, T., Wierstra, D., & Riedmiller, M. (2014). Deterministic Policy Gradient Algorithms. Proceedings of the 31st International Conference on Machine Learning (ICML-14), 387–395.][7]

<!-- Links -->
[BipedalWalker-v2]: https://gym.openai.com/envs/BipedalWalker-v2
[gym]:              https://github.com/openai/gym
[keras]:            https://github.com/fchollet/keras
[matplotlib]:       https://matplotlib.org/
[sklearn]:          http://scikit-learn.org/stable/
[tf]:               https://www.tensorflow.org/

[1]: https://arxiv.org/abs/1502.03167
[2]: http://web.mit.edu/jnt/www/Papers/J094-03-kon-actors.pdf
[3]: https://arxiv.org/pdf/1509.02971.pdf
[4]: https://storage.googleapis.com/deepmind-media/dqn/DQNNaturePaper.pdf
[5]: https://www.cs.toronto.edu/~vmnih/docs/dqn.pdf
[6]: https://arxiv.org/pdf/1703.03864.pdf
[7]: http://proceedings.mlr.press/v32/silver14.pdf
