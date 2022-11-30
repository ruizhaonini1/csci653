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

Key idea

Automorphism

Automorphism is used to rearrange the ciphertext based on the rotation step k. The result is the special permutations of the coefficients of the ciphertext polynomials. 
For every iteration in the Automorphism, it will read element one by one, and then based on the rotation step, it computes the corresponding index of the output array, write the element to this index.

NTT Parallelization

NTT computation have three parts: loading related data, performing arithmetic computations and sorting the result
With each PE (so called butterfly units) execute arithmetic computation, and multiplication
To achieve a higher throughput, it is possible to unroll NTT loops and parallelize the butterfly operations using multiple PEs


An n-pt NTT operation consists of log2n stages in each of which (n/2) butterfly operations are performed.
An NTT operation can be parallelized by performing multiple butterfly operations concurrently. The input of an NTT stage is the output of the previous NTT stage, 
Thus, an NTT operation has limited parallelism for a given input, at most (n/2) butterfly operations can be performed in parallel

Butterfly Unit
The proposed design uses the Iterative NTT scheme of which consists of log2 n stages and performs(n/2) butterfly operations at each stage. Here is an example of the memory read access pattern of coefficients for n=8
Each yellow dot represents a butterfly operation, which consumes and produces two coefficients mapping to the same degree.



![image](https://user-images.githubusercontent.com/74476225/204872801-c47e975f-e53b-46fe-b290-128c8ad731e6.png)

















