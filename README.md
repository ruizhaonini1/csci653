# csci653
FPGA Acceleration of Homomorphic Rotation![image](https://user-images.githubusercontent.com/74476225/204866795-401ba1c7-e408-45d4-bac0-c86377a865f7.png)

1. HE(Homomorphic Encryption) can provide protection to clients when they are sending data to the cloud 

2. But the high computation complexity and latency of the HE schemes still form the bottleneck for applications. 
![image](https://user-images.githubusercontent.com/74476225/204867746-71dc8f87-6ddf-4989-879a-9965b67d13e5.png)

Objective:

For HE rotation, there are two main stages: NTT and automorphism, these two algorithms take up the most proportion of the computations 
In this project, I tried to parallelize these two algorithm, and get their performance(latency and resources). Based on the results, it can project the main performance of the HE rotation.
After the optimization of these two algorithms, I will increase the performance of the HE rotation


Challenges:
The parallelization for these two algorithm is not straightforward
First, the automorphism algorithm is a rearrangement for the ciphertext which need complex data communication between computation stages. 
Second, the modular multiplication in NTT is usually resource-consuming and slow. The high resource requirements of modular arithmetic are needed for designing the low latency NTT cores. 
There are others work which related to these two algorithms, but they use the Verilog to accelerate it and not the Xilinx HLS.

Project Parallelization Hypothesis:

For the Automorphism algorithm I assume that using loop unroll can reduce the computation time and using on-chip SRAM can reduce the off-chip memory access

For NTT part, I assume that implementing and parallelizing the butterfly unit to increases the parallelism and the performance of the operation.

Key idea![image](https://user-images.githubusercontent.com/74476225/204869380-f03fa237-a9e1-4bf6-9ee0-237761691ef8.png)
![image](https://user-images.githubusercontent.com/74476225/204869406-f9e88cff-544e-4c88-9c71-db2ea50d4187.png)













