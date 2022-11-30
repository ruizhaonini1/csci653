# csci653
FPGA Acceleration of Homomorphic Rotation![image](https://user-images.githubusercontent.com/74476225/204866795-401ba1c7-e408-45d4-bac0-c86377a865f7.png)

1. HE(Homomorphic Encryption) can provide protection to clients when they are sending data to the cloud 

2. But the high computation complexity and latency of the HE schemes still form the bottleneck for applications. 
![image](https://user-images.githubusercontent.com/74476225/204867746-71dc8f87-6ddf-4989-879a-9965b67d13e5.png)

Objective![image](https://user-images.githubusercontent.com/74476225/204867815-ec458fe4-caed-488b-8a0f-5a7a38862d79.png)
For HE rotation, there are two main stages: NTT and automorphism, these two algorithms take up the most proportion of the computations 
In this project, we trying to parallelize these two algorithm, and get their performance(latency and resources). Based on the results, we can project the main performance of the HE rotation.
After the optimization of these two algorithms, we will increase the performance of the HE rotation
![image](https://user-images.githubusercontent.com/74476225/204867839-828267af-d5ce-4197-9240-c6ec20ee48cf.png)






