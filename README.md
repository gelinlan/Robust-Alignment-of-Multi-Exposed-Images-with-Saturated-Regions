Robust-Alignment-of-Multi-Exposed-Images-with-Saturated-Regions
=========

Jun JIANG, Zhengguo LI, Shiqian WU, Liangcai ZENG and Shoulie XIE <br>
Wuhan University of Science and Technology, Wuhan, 430081, China <br>
{jiangjun85, zengliangcai, shiqian.wu} @wust.edu.cn  <br>
The Institute for Infocomm Research, Singapore, 138632 <br>
{ezgli, slxie}@i2r.a-star.edu.sg <br>

**Abstract:** It is challenging to align multi-exposed images due to large illumination variations, especially in presence of saturated regions. In this paper, a novel image alignment algorithm is proposed to cope with the multi-exposed images with saturated regions. Specifically, the multi-exposed images are first normalized by using intensity mapping functions (IMFs) in consideration of saturated pixels. Then, the normalized images are coded by using the local binary pattern (LBP). Finally, the coded images are aligned by formulating an optimization problem by using a differentiable “Hamming” distance. Experimental results show that the proposed algorithm outperforms state-of-the art alignment methods for multi-exposed images in terms of alignment accuracy and robustness to exposure values.

# Challenges:

Multi-exposed images contain saturated regions, leading the huge differences between images.

LBP code does not capture the closeness of two bit-strings and it is sensitive to the rotation.

For binary descriptor, hamming distance is non-differentiability and unsuitable for optimization.

# The proposed method:

![](https://github.com/gelinlan/Robust-Alignment-of-Multi-Exposed-Images-with-Saturated-Regions/blob/master/Fig1.jpg)

# Effect of intensity mapping function (IMF)
![](https://github.com/gelinlan/Robust-Alignment-of-Multi-Exposed-Images-with-Saturated-Regions/blob/master/Fig2.jpg)

# Effect of feature description
![](https://github.com/gelinlan/Robust-Alignment-of-Multi-Exposed-Images-with-Saturated-Regions/blob/master/Fig3.jpg)


# Experimental Results
The proposed method is evaluated with a variety of synthesized images from benchmark datasets, public datasets s and real images. The proposed method are compared with 1) existing non-parametric ordering features using MTB [3], CT [4], LBP [5] and BRIEF [6] methods, while employing the alignment algorithm shown in Section III; 2) the intensity-based IMF; 3) the feature-based method SIFT [7] and the hybird method IMF+SIFT; 4) IMF+BRIEF and IMF+BRIEF+“Hamming” distance (“HD”); 5) IMF+LBP [1]. 6) Learning-based matching methods SuperPoint [8] and LF-Net [9].
## Tests on synthesized sequences
To evaluate the robustness to exposure, the first image is selected as the reference and other images are rotated by 50, and shifted 30 pixels and 10 pixels in y-axis and x-axis respectively. Table1-2 are the motion errors on benchmark and public database. The average errors of the proposed method is the smallest, which implies the proposed method is suitable for various scene sets alignment and robust to intensity variations. Tables 3-6 summarize the motion errors on “Snowman”, “BigTree”, “Pillar” and “Inscription” sequences. 
TABLE 1. Overall results performed on benchmark database. 
![](https://github.com/gelinlan/Robust-Alignment-of-Multi-Exposed-Images-with-Saturated-Regions/blob/master/table1.jpg)
TABLE 2: Overall results performed on 40 Cai’s database
![](https://github.com/gelinlan/Robust-Alignment-of-Multi-Exposed-Images-with-Saturated-Regions/blob/master/table2.jpg)
![](https://github.com/gelinlan/Robust-Alignment-of-Multi-Exposed-Images-with-Saturated-Regions/blob/master/table3.jpg)
![](https://github.com/gelinlan/Robust-Alignment-of-Multi-Exposed-Images-with-Saturated-Regions/blob/master/table4.jpg)
![](https://github.com/gelinlan/Robust-Alignment-of-Multi-Exposed-Images-with-Saturated-Regions/blob/master/table5.jpg)
![](https://github.com/gelinlan/Robust-Alignment-of-Multi-Exposed-Images-with-Saturated-Regions/blob/master/table6.jpg)
![](https://github.com/gelinlan/Robust-Alignment-of-Multi-Exposed-Images-with-Saturated-Regions/blob/master/Fig4.jpg)
## Tests on Real sequences
As motion parameters are unknown, the alignment results are evaluated in terms of mutual information (MI)[10], which is a successful measure for registering multi-modal images. Selecting the brightest image as reference, the MIs based on the 35 real sequences in file “Real sequences” are shown below.
It is noted that the MI values are different for various scenarios due to different contents (static/ dynamic scenes, little/severe saturation, and different EVs etc.), even the alignment performance is the same. But the performance comparison in terms of MI for the identical scene is meaningful.

## Tests on Efficiency
![](https://github.com/gelinlan/Robust-Alignment-of-Multi-Exposed-Images-with-Saturated-Regions/blob/master/table7.jpg)
![](https://github.com/gelinlan/Robust-Alignment-of-Multi-Exposed-Images-with-Saturated-Regions/blob/master/table8.jpg)
