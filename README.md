# csci653
FPGA Acceleration of Homomorphic Rotation![image](https://user-images.githubusercontent.com/74476225/204866795-401ba1c7-e408-45d4-bac0-c86377a865f7.png)

1. HE(Homomorphic Encryption) can provide protection to clients when they are sending data to the cloud 

2. But the high computation complexity and latency of the HE schemes still form the bottleneck for applications. 
![image](https://user-images.githubusercontent.com/74476225/204867746-71dc8f87-6ddf-4989-879a-9965b67d13e5.png)

Objective
For HE rotation, there are two main stages: NTT and automorphism, these two algorithms take up the most proportion of the computations 
In this project, I tried to parallelize these two algorithm, and get their performance(latency and resources). Based on the results, it can project the main performance of the HE rotation.
After the optimization of these two algorithms, I will increase the performance of the HE rotation







