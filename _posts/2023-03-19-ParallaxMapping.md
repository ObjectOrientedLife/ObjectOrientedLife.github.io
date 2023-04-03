---
title: "Parallax Mapping"
categories: 
    - Game Project
---

## Introduction
Had it not been for the bump mapping technique including normal mapping, game developers would have been forced to choose between two unsatisfactory options; to subdivide to add 'real' details and get millions of billions of vertex count, or to just give up any details, leaving only tedious low-poly surfaces. Thanks to bump mapping techniques including normal mapping, we can keep details without pressing the 'subdivision' button three or more times.

Normal mapping does yield outstanding results as [Fig. 1]. As you might have expected, normal mapping is not perfect. If it were, why would high-poly models be so popular in AAA games? The problematic situation for a plane with a normal map applied happens when you view the plane from a steep angle(that is, the normal vector ***n*** and the view vector ***v*** are diverged by a large amount). As the angle between ***n*** and ***v*** gets larger, the normal map rapidly loses its 'bump power' and looks planar.

I found this trouble from my sandbags fortification model. Look at the flat surface of the stacked sandbags when viewed from the side! I couldn't stand the poor quality of bumps, and started to find out if there was any way to mitigate it.

## Parallax Mapping

### What is **parallax mapping**?

**Parallax mapping** is a mapping technique to create the illusion of depth on a flat surface introduced by [1]. It is a form of displacement mapping that simulates the effect of parallax, which is the apparent shift in position of an object when viewed from different angles. In parallax mapping, the texture applied to a surface is displaced in a way that simulates the bump of the surface.



### How does it work? 

Parallax mapping shifts the texture coordinate to approximate 'the real height' as below. For simplicity, let's assume that $o$ is located at the origin.

1. We are given;
    * $o = (0, 0, 0)$ : Texture coordinate that would be sampled if we didn't use the parallax mapping
    * $h$: Height given by sampling the height map at $o$
    * $v$: View vector
2. Get the plane $f$ with the normal vector $n$ that is tangent to the surface of the height map.
3. The point $p$ where $v$ and $f$ intersects is the approximation of the real intersecting point of $v$ and the height map surface.
4. Sample the texture at $p_{xy}$



Then, how can we get the point $p$, assuming we have knowledge of plane equation?

1. We can easily figure out the plane equation $f = n_xx + n_yy + n_zz + d$.

2. Since $o + (0, 0, h)$ is on $f$, we can figure out $d = -n_zh$

3. Let $p = o + tv$. Now we have to figure out what the value of $t$ is.

4. Beware that  $p = o + tv$ is also a point on $f$. Therefore the following mathematical expressions holds.
   $$
   tn_xv_x + tn_yv_y + tn_zv_z - n_zh = 0 \\
   t(n_xv_x + n_yv_y + n_zv_z) = n_zh \\
   t = \frac{n_zh}{n_xv_x + n_yv_y + n_zv_z} = \frac{n_zh}{n \cdot v}
   $$

5. We now have $p = o + tv = o + \frac{n_zh}{n \cdot v}v$



Conclusion! We just offset the initial coordinate by $\frac{n_zh}{n \cdot v}$ along $v$ to get the point over the adjusted sampling coordinate that we intended.



### Adjustments

When $n$ and $v$ are almost perpendicular, $n \cdot v$ gets very close to zero, in which case the offset $t$ can grow arbitrarily large. [2] multiplies $t$ by $n \cdot v$ to remove the denominator in order to avoid such erroneous situations.



## Evaluation

## Conclusion