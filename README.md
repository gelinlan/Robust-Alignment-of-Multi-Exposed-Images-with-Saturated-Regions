Robust-Alignment-of-Multi-Exposed-Images-with-Saturated-Regions
=========

Jun JIANG, Zhengguo Li, Shiqian WU, Liangcai ZENG and Shoulie XIE <br>
Wuhan University of Science and Technology, Wuhan, 430081, China <br>
{jiangjun85, zengliangcai, shiqian.wu} @wust.edu.cn  <br>
The Institute for Infocomm Research, Singapore, 138632 <br>
{ezgli, slxie}@i2r.a-star.edu.sg <br>

**Abstract:** It is challenging to align multi-exposed images due to large illumination variations, especially in presence of saturated regions. In this paper, a novel image alignment algorithm is proposed to cope with the multi-exposed images with saturated regions. Specifically, the multi-exposed images are first normalized by using intensity mapping functions (IMFs) in consideration of saturated pixels. Then, the normalized images are coded by using the local binary pattern (LBP). Finally, the coded images are aligned by formulating an optimization problem by using a differentiable “Hamming” distance. Experimental results show that the proposed algorithm outperforms state-of-the art alignment methods for multi-exposed images in terms of alignment accuracy and robustness to exposure values.

# Challenges:

Multi-exposed images contain saturated regions, leading the huge differences between images.

LBP code does not capture the closeness of two bit-strings and it is sensitive to the rotation.

For binary descriptor, hamming distance is non-differentiability and unsuitable for optimization.

