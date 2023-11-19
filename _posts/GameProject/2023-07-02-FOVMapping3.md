---
title: "FOV Mapping (3)"
categories: 
    - Game Project
---

# Introduction

We have pushed the envelope to design, implement, and improve FOV mapping system, but that does not guarantee that FOV mapping will work correctly on every environment. So, let's prove its validity with diverse tests.

# Environment

All the assessments except for compatibility test were run on my laptop(Lenovo Thinkbook 16p Gen 1) that features the following specification.

* AMD Ryzen 7 5800H
* NVIDIA GeForce RTX 3060 Laptop GPU
* 16GB RAM

# Qualitative Evaluation

## FOV Map Generation Time

One weakness of FOV mapping is that it requires a long time to generate an FOV map. As a matter of course, the times taken to generate an FOV map vary according to the number of layers and resolution of a texture. The purpose of this test is to clarify how long you have to endure if you want to adopt FOV mapping. Each case was run five times and averaged.

| Resolution  |   Map 1    |    Map2    |
| :---------: | :--------: | :--------: |
|  128 x 128  |  48.8 sec  | 101.5 sec  |
|  256 x 256  | 195.7 sec  | 421.3 sec  |
|  512 x 512  | 823.6 sec  | 1732.6 sec |
| 1024 x 1024 | 2957.4 sec | 7498.8 sec |

Interestingly, the consequences differ by about two times between the two maps. This is because the number of rays cast is different due to a few factors; the number of hit rays, stop sampling when a vertical surface is encountered, and many others. Within the same map, the times taken are proportional to the resolution.

## Performance Comparison

Now, our aim is at whether we have achieved our initial goal; high-performance field of view backed by a massive crowd. To prove that FOV mapping is superior to raycasting method when a large number of eyes are involved, we compare the FPS of the two methods by doubling the number of agents each time.

For a fair comparison, the conditions were set a little bit artificially.

**Raycasting**

* Fire 36 rays
* Conduct two binary search iteration per obscure edge

**FOV Mapping**

* Use 90 1024x1024 layers
* No enemy occluded by the fog of war

For the test, I measured framerate for one minute each and took average. After conducting a round of trial, I got the results below.

| Agent Count | Raycasting | FOV Mapping | FPS Ratio |
| :---------: | :--------: | :---------: | :-------: |
|      1      | 1473.5 FPS | 1678.4 FPS  |   1.14    |
|      2      | 1223.4 FPS | 1586.7 FPS  |   1.30    |
|      4      | 1215.3 FPS | 1564.1 FPS  |   1.29    |
|      8      | 1046.6 FPS | 1491.9 FPS  |   1.43    |
|     16      | 876.4 FPS  | 1453.1 FPS  |   1.66    |
|     32      | 540.1 FPS  | 1306.2 FPS  |   2.42    |
|     64      | 265.8 FPS  | 1125.6 FPS  |   4.23    |
|     128     |  67.5 FPS  |  365.7 FPS  |   5.42    |

 The table demonstrates an evident superiority of FOV mapping as we add more and more agents to a scene.

# Quantitative Evaluation

## Video

{% include video id="odzodrk1F7k" provider="youtube" %}
