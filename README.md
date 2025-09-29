# Diversity Is All You Need (DIAYN) Implementation using RLkit

Implementation of Proximal Diversity Is All You Need (DIAYN) using the reinforcement learning framework [RLKit](https://github.com/vitchyr/rlkit) by [vitchyr](https://github.com/vitchyr).
Installation for RLKit is specified in the [original README for RLKit](README_RLKIT.md).

 - Diversity Is All You Need (DIAYN)
    - [Example script](examples/diayn.py)
    - [Paper](https://arxiv.org/abs/1802.06070)

 - Proximal Policy Optimization (PPO)
    - [Example script](examples/ppo.py)
    - [Paper](https://arxiv.org/abs/1707.06347)
    - Other References
      - [SpinningUp documentation](https://spinningup.openai.com/en/latest/algorithms/ppo.html)
      - [Lilian Weng's blog](https://lilianweng.github.io/lil-log/2018/04/08/policy-gradient-algorithms.html#ppo)

### Running the Example Script for DIAYN
First, run the following command for training the sub-policies:
```
python examples/diayn.py <NAME_OF_ENVIRONMENT>
```

In addition, you can specify the number of skills that DIAYN is going to learn. The default is set at 10.
```
python examples/diayn.py <NAME_OF_ENVIRONMENT> --skill_dim <NUMBER_OF_SKILLS>
```

After training DIAYN, a file is saved onto `data/DIAYN_<NUMBER_OF_SKILLS>_<ENVIRONMENT>_<DATE_AND_TIME>`. Use the saved file to train the manager using PPO.
```
python examples/ppo_diayn.py <NAME_OF_ENVIRONMENT> <PATH_TO_SUB_POLICY>/params.pkl
```

Run the following command for visualizing the trained policies:
```
python scripts/run_policy_diayn.py <PATH_TO_SUB_POLICY>/params.pkl
```
Here is an example implementation result on the OpenAI Gym environment, Bipedal Walker-v2:
[![example video](https://img.youtube.com/vi/via75gSmvTc/hqdefault.jpg)](https://www.youtube.com/watch?v=via75gSmvTc)

Intrinsic Reward Learning Curve:
![intrinsic reward learning curve](docs/images/diayn_intrinsic_rewards.png)

Policy Loss Learning Curve:
![intrinsic reward learning curve](docs/images/diayn_policy_loss.png)

### Running the Example Script for PPO
Run the following command:
```
python examples/ppo.py
```
Here is an example implementation result on the OpenAI Gym environment, Bipedal Walker-v2:

[![example video](https://img.youtube.com/vi/zf0sh0jtIWU/hqdefault.jpg)](https://www.youtube.com/watch?v=zf0sh0jtIWU)



### Other Major Contributors
 - [seann999](https://github.com/seann999)
