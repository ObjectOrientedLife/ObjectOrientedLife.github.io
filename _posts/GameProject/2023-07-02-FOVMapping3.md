---
title: "FOV Mapping (3)"
categories: 
    - Game Project
---

# Introduction

We have pushed the envelope to design, implement, and improve FOV mapping system, but that does not guarantee that FOV mapping will work correctly on every environment. So, let's prove its validity with diverse tests.

# Environment

All the assessments except for compatibility test were run on my laptop(Lenovo Thinkbook 16p Gen 1) that features the following specification.

* AMD Ryzen™ 7 5800H
* NVIDIA GeForce RTX 3060 Laptop GPU
* 16GB RAM

# Qualitative Evaluation

## FOV Map Generation Time

One weakness of FOV mapping is that it requires a long time to generate an FOV map. As a matter of course, the times taken to generate an FOV map vary according to the number of layers and resolution of a texture. The purpose of this test is to clarify how long you have to endure if you want to adopt FOV mapping. Each case was run five times and averaged.

| Resolution  |   Map 1    |    Map2    |
| :---------: | :--------: | :--------: |
|  128 x 128  |  38.8 sec  |  72.5 sec  |
|  256 x 256  | 142.7 sec  | 261.3 sec  |
|  512 x 512  | 573.6 sec  | 1132.6 sec |
| 1024 x 1024 | 2354.1 sec | 4066.8 sec |

Interestingly, the consequences differ by about two times between the two maps. This is because the number of rays cast is different due to a few factors; the number of hit rays, stop sampling when a vertical surface is encountered, and many others. Within the same map, the times taken are proportional to the resolution.

## Performance Comparison

Now, our aim is at whether we have achieved our initial goal; high-performance field of view backed by a massive crowd. To prove that FOV mapping is superior to raycasting method when a large number of eyes are involved, we compare the FPS of the two methods by doubling the number of agents each time.

For a fair comparison, the conditions were set a little bit artificially.

**Raycasting**

* Fire 36 rays
* Conduct two binary search iteration per obscure edge

**FOV Mapping**

* Use 90 1024x1024 layers
* Gaussian blur is disabled

For the test, I measured framerate for one minute each and took average. After conducting a round of trial, I got the results below.


| Agent Count | Raycasting | FOV Mapping | FPS Ratio |
| :---------: | :--------: | :---------: | :-------: |
|      1      | 1461.5 FPS | 1937.2 FPS  |   1.33    |
|      2      | 1139.1 FPS | 1925.8 FPS  |   1.69    |
|      4      | 993.1 FPS  | 1855.1 FPS  |   1.87    |
|      8      | 650.2 FPS  | 1749.5 FPS  |   2.69    |
|     16      | 493.2 FPS  | 1564.6 FPS  |   3.17    |
|     32      | 279.8 FPS  | 1450.7 FPS  |   5.18    |
|     64      | 161.5 FPS  | 1390.6 FPS  |   8.61    |
|     128     |  80.9 FPS  |  409.5 FPS  |   5.06    |

 The table demonstrates an evident superiority of FOV mapping as agents populate.

# Quantitative Evaluation

