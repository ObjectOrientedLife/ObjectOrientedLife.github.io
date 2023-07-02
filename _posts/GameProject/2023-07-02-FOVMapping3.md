# Introduction

We have pushed the envelope to design, implement, and improve FOV mapping system, but that does not guarantee that FOV mapping will work correctly on every environment. So, let's prove its validity with diverse tests.

# Environment

All the tests were run on my laptop(Lenovo Thinkbook 16p Gen 1) that features the following specification.

* AMD Ryzen™ 7 5800H
* NVIDIA GeForce RTX 3060 Laptop GPU
* 16GB RAM

# FOV Map Generation Time

One weakness of FOV mapping is that it requires a long time to generate an FOV map. As a matter of course, the times taken to generate an FOV map vary according to the number of layers and resolution of a texture. The purpose of this test is to clarify how long you have to endure if you want to adopt FOV mapping. Each case was run five times and averaged.

## Resolution

## Number of Layers

# Qualitative Evaluation

# Performance Comparison

Now, our aim is at whether we have achieved our initial goal; high-performance field of view backed by a massive crowd. To prove that FOV mapping is superior to raycasting method when a large number of eyes are involved, we compare the FPS of the two methods by doubling the number of agents each time.

| Agent count | Raycasting | FOV mapping |
| ----------- | ---------- | ----------- |
| 1           | 128 FPS    |             |
| 2           |            |             |
| 4           |            |             |
| 8           |            |             |
| 16          |            |             |
| 32          |            |             |
| 64          |            |             |
| 128         |            |             |

 

