# Maximise Network Capacity

#### Description
Code# 2024 Problem 

## Problem Statement
Code#'s Wifi Network is allowed to transmit signals at a particular frequency range ($F_1$ MHz, $F_2$ MHz). This frequency range is then further divided into sub-frequency ranges $R$ to reduce network interference due to overlapping channels. 

The **bandwidth** of a particular frequency range is given by $F_{max} - F_{min}$. 

The frequency ranges **may not** be evenly distributed across the sub-ranges of a network, which also means that network bandwidth may not be evenly distributed. For example, a sub-range $R$ = [(5000 MHz, 5100 MHz), (5100 MHz, 5300 MHz), (5300 MHz, 5315 MHz)] is a valid range. Then the bandwidth of each sub-range would be 100 units (5100 - 5000), 25 units (5300 - 5100) and 15 units respectively. 


A particular device on the network can use a single frequency range or **multiple contiguous frequency ranges**. The Code#'s Wifi Network now consists of $D$ such devices.

If the maximum **bandwidth** $B_{max}$ allocated to a particular device on the network is **minimised**, then the network capacity is maximised. Let's consider an example below: 

Suppose if $D = 2$ and $R$ = [(5000 MHz, 5100 MHz), (5100 MHz, 5300 MHz), (5300 MHz, 5315 MHz)], then we have two ways of dividing the network channels.

1. Device 1 takes (5000 MHz, 5300 MHz) (ie. merge $R[0]$ and $R[1]$ into a single range) and Device 2 takes (5300 MHz, 5315 MHz). This causes Device 1 to have the largest bandwidth in the network of 300 units. Hence $B_{max} = 300$

2. Device 1 takes (5000 MHz, 5100 MHz) and Device 2 takes (5100 MHz, 5315 MHz) (ie. merge $R[1]$ and $R[2]$ into a single range). This causes Device 1 to have a bandwidth of 100 MHz, and Device 2 has a largest bandwidth in the network of 215 MHz. Hence, $B_{max} = 215$.

Since option 2 minimises the largest bandwidth allocated to 1 device, the network capacity across all devices is maximized. 

Given a list of $N$ frequency ranges in a list $R$ and a value for $D$, return the smallest possible value for $B_{max}$. If such a task is not possible, then output -1.

#### Input Format
The first line contains two integers separated by a space: the value of $D$ followed by the value of $N$. 

The next $N$ lines consists of 2 integers each, separated by a space. The $i$-th row represents the value for $R[i]_{min}$ followed by the value for $R[i]_{max}$ of the frequency range $i$.

#### Constraints
- $1 \leq D, N \leq 10^6$
- $1 \leq R[i]_{min} \leq R[i]_{max} \leq 10^6$
- $R[i]_{min} = R[i-1]_{max} \text { for all } i \geq 1$
- $\sum_{r \in R} (r_{max} - r_{min}) \leq 2^{31}-1$ (ie. will fit into the range of a 32-bit signed integer.)

#### Output Format
A single integer $B_{max}$, denoting the maximum bandwidth allocated to a device while maximising the network capacity.

#### Sample Input 0
```
2 3
5000 5100
5100 5300
5300 5315
```
#### Sample Output 0
```
215
```

##### Explanation
Same example as the question.

#### Sample Input 1
```
3 3
5000 5100
5100 5300
5300 5315
```
#### Sample Output 1
```
200
```

##### Explanation
Since $D = 3$ and $N = 3$, we can only allocate 1 device to 1 frequency range in order for the network to support all 3 devices. This means that $B_{max}$ is the bandwidth of the largest range (range 1).  