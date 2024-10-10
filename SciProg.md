Chapter 2
We compute modest approximations for $\pi$ using two different ideas

1. We will cover the circle $x^2+y^2=n^2$ with 1x1 square tiles. If N is the number of tiles that are *completely within* the circle, then from the approximation of $$\pi n^2 \approx N ~~\Rightarrow~~ \pi \approx \frac{N}{n^2}$$ Where we really just use the total number of tiles to estimate $\pi$
2. We can approximate the unit circle with a polygon and regard the polygon area as an approximation of $\pi$. 
	1. For a given n, a good approximating polygon is the regular n-gon whose edges are tangent (circumscribed) to the unit circle, then this area will be an overestimation of $\pi$. 
	2. Conversely, for an underestimation of $\pi$, a good approximating polygon is the regular n-gon whose vertices (inscribed) are on the unit circle.  ![Circumscribe and Inscribe Figures](https://external-content.duckduckgo.com/iu/?u=https%3A%2F%2Ftse2.mm.bing.net%2Fth%3Fid%3DOIP.eAu_jXVVmAd-wtJHE7IcYwHaFP%26pid%3DApi&f=1&ipt=c335aa471943603b76c46cb8d46c94cbdfe58e3c302910e94ce24f039ee08cb9&ipo=images)

# Tiling a Disk
Suppose n is a positive integer and we draw the circle $x^2 + y^2 = n^2$ on graph paper that has 1 x1 squares. 
![基于遗传算法的农业无线传感器节点部署算法设计_参考网](https://external-content.duckduckgo.com/iu/?u=https%3A%2F%2Fcimg.fx361.com%2Fimages%2F2022%2F1123%2Ffd5370c664da4099eae17875f7df842067a909cb.webp&f=1&nofb=1&ipt=92289edd4a060048948da09737feda03cb90ae2e16d05c59f7a2c1e537bcfa0c&ipo=images)
Note that since radius of the disk, $r = n$, the area of the disk is $\pi n^2$.  Also each uncut tile as area 1 unit$^2$. ***If*** there are N uncut tiles, then we can conclude that $$N \approx \pi n^2$$ since the uncut tiles almost cover the disk. We will write a script that inputs the number of tiles, n, and displays the $\pi$ approximation.
$$\rho_n = \frac{N}{n^2}$$ together with the error: $|\rho_n - \pi|$

- Because of symmetry, each quadrant is the same, so we can take 1/4 of the circle. We only need to count the number of uncut tiles in the first quadrant
	- If $N_1$ is the number of uncut tiles in the first quadrant, then $$\rho_n = \frac{4N}{n^2}$$
		- This is because area, in this case is given by $4\rho_n n^2$.
	- To compute $N_1$ we sum the number of uncut tiles that are located in each horizontal row. 
		- We see there are 9 uncut tiles in rows 1,2,3,4
		- There are 8 uncut tiles in rows 5,6
		- and 7 uncut tiles in rows 7....
	- We need to update the running sum N_1 for each set of uncut tiles.
	- For a specific value of n, we can implement a solution 