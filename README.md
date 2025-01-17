# Computer-vision-HW1-Pet-edge-detection

As you know, this course is largely funded by grants from Petco, Inc.TM One of the strings attached to this funding is the occasional sponsored problem where, regrettably, we must provide a problem that has substantial industrial implications for our sponsor1. Our friends at Petco see an opportunity to use computer vision to pull ahead of their rivals, PetsmartTM, with whom they are locked in bitter competition. Rather than laboriously marking the edges of dogs and cats in pictures by hand—the current industry practice—they have turned to you.

(a) Using the starter code provided, apply the horizontal and vertical gradient ﬁlters [1, -1] and [1,−1]> to the picture of the provided pet, producing ﬁlter responses Ix and Iy. Write a function convolve(im, h) that takes a grayscale image and a 2D ﬁlter as input, and returns the result after convolution. Please do not use any “black-box” ﬁltering functions for this (such as the ones in scipy). Instead, implement the convolution as a series of nested for loops (you may also use numpy.dot, but it is not necessary). Compute the total edge strength as I2 x + I2 y, and visualize it using matplotlib, following the sample code. Create visualizations of Ix, Iy, and the combined response, following the sample code.
Please handle out-of-bounds pixels in the image by assuming that they are 0. Also please make sure to implement convolution, not cross-correlation. Note that this simple ﬁltering method will have a fairly high error rate — there will be true object boundaries it misses and spurious edges that it erroneously detects. The team at Petco, thankfully, has volunteered to manually ﬁx any errors (2 points).

(b) (Optional) This method detects edges fairly well on one of the dogs, but not the other. Our sponsor would like us to investigate why this is happening. First, convert your gradient outputs to edge detections using a hand-chosen threshold τ (i.e. set values at most τ to 0 and those above to 1). Point out 2 errors in the resulting edge map — that is, edge detections that do not correspond to the boundary of an object — and explain what causes these errors (0 points).


(c) While the edge detector you submitted works well on some pets, engineers are reporting a large number of failures, and Petco execs are not happy. Rumor is that it’s failing on pets that are playing in grass, especially for dogs with ﬂuﬀy coats (Figure 1b) — a particularly lucrative market for our sponsor. It appears that the gradient ﬁlter is ﬁring on small, spurious edges.
Kindly address our funders’ problem by creating an edge detector that only responds to larger-scale edges. Do this by ﬁrst blurring the image with a Gaussian ﬁlter, before computing gradients. Implement both the Gaussian ﬁlter and the gradient ﬁlter using a black-box convolution function scipy.ndimage.convolve, rather than your hand-crafted solution.

(i) Compute the edges without blurring, so we can look at the before-and-after results.
(ii) Compute the blurred image using σ = 2 and an 11×11 ﬁlter. 
(iii) Instead of blurring the image with a Gaussian ﬁlter, use a box ﬁlter (i.e., set each of the 11×11 ﬁlter values to 1/112). 
(iv) Compute edges on the two blurred images.
(v) (Optional) Do you see artifacts in the box-ﬁltered result? Describe how the two results diﬀer. Include your written response in the notebook.
Visualize the edges in the same manner as Problem 1.2(a). 

Your notebook should contain edges that were computed using no blurring, Gaussian blurring, and box ﬁltering. Please also show the two blurred images (2 points).


(d) Instead of convolving the image with two ﬁlters to compute Ix (i.e. a Gaussian blur followed by a gradient), create a single ﬁlter that yields the same response. Visualize the ﬁlter using the provided code (1 point).
(e) Good news: Petco execs are pleased with your work, and they’ve renewed our funding for several more problem sets. At our last grant meeting, however, they made an additional request. Their competitors at Petsmart are now computing oriented edges of their pets: rather than just estimating just the horizontal or the vertical gradients, they now provide gradients for an arbitrary angle θ. Petsmart’s method for doing this, however, is computationally expensive: they construct a new ﬁlter for each angle, and ﬁlter the image with it. Petco sees an opportunity to beat Petsmart at their own game using steerable ﬁlters.
Write a function oriented grad(Ix,Iy,θ) that returns the image gradient in the direction θ, given the horizontal and vertical gradients. Use this function to compute gradients for the provided sample image at θ ∈{1 4π, 1 2π, 3 4π}. Compute your gradients on a blurred version of the input image, using the same blur kernel as (c). Visualize these results in the same manner as Problem 1.2 (a) (1 point).
