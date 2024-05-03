# Deep Q Learning For Lunar Lander

## Introduction

This is going to be a modelled version of a spaceship but still - it will learn how to lands itself on the moon. 
And the key word here is learn, because the spaceship will not be given any rules on how to operate in the environment before hand - it will have to figure everything out on it's own. 
This functionality will be achieved with Deep Q-Learning. Deep Q-Learning is the result of combining Q-Learning with an Artificial Neural Network. 
The states of the environment are encoded by a vector which is passed as input into the Neural Network. 
Then the Neural Network will try to predict which action should be played, by returning as outputs a Q-value for each of the possible actions. 
Eventually, the best action to play is chosen by either taking the one that has the highest Q-value, or by selecting one at random with a strategy called epsilon-greedy, which is used for exploration.

## Preview
https://github.com/CoboAr/Deep-Q-Learning-for-Lunar-Landing/assets/144629565/cc78aef4-6838-4c0f-a358-94a815a380ae

## Requirements 
 Google Colab       
 [Gymnasium Documentation Lunar Lander](https://gymnasium.farama.org/environments/box2d/lunar_lander/)      
 PyTorch

## Environment Description
This environment is a classic rocket trajectory optimization problem. According to Pontryagin’s maximum principle, it is optimal to fire the engine at full throttle or turn it off. 
This is the reason why this environment has discrete actions: engine on or off. There are two environment versions: discrete or continuous. 
The landing pad is always at coordinates (0,0). The coordinates are the first two numbers in the state vector. Landing outside of the landing pad is possible. 
Fuel is infinite, so an agent can learn to fly and then land on its first attempt.

## Action Space
There are four discrete actions available:
<ul>
  <li>0: do nothing</li>
  <li>1: fire left orientation engine
  <li>2: fire main engine</li>
  <li>3: fire right orientation engine</li>
</li>
</ul>

## Observation Space 
The state is an 8-dimensional vector: the coordinates of the lander in x & y, its linear velocities in x & y, its angle, its angular velocity, and two booleans that represent whether each leg is in contact with the ground or not.

## Rewards
After every step a reward is granted. The total reward of an episode is the sum of the rewards for all the steps within that episode.

For each step, the reward:
<ul>
  <li>is increased/decreased the closer/further the lander is to the landing pad.</li>
  <li>is increased/decreased the slower/faster the lander is moving.</li>
  <li>is decreased the more the lander is tilted (angle not horizontal).</li>
  <li>is increased by 10 points for each leg that is in contact with the ground.</li>
  <li>is decreased by 0.03 points each frame a side engine is firing.</li>
  <li>is decreased by 0.3 points each frame the main engine is firing.</li>
</ul>
The episode receives an additional reward of -100 or +100 points for crashing or landing safely respectively.

An episode is considered a solution if it scores at least 200 points.

## Starting State
The lander starts at the top center of the viewport with a random initial force applied to its center of mass.

## Episode Termination
The episode finishes if:
<ol>
<li>the lander crashes (the lander body gets in contact with the moon);</li>
<li>the lander gets outside of the viewport (x coordinate is greater than 1);</li>
<li>the lander is not awake. From the Box2D docs, a body which is not awake is a body which doesn’t move and doesn’t collide with any other body:</li>
</ol>


Enjoy! And please do let me know if you have any comments, constructive criticism, and/or bug reports.
## Author
## Arnold Cobo

