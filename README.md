Robust-Alignment-of-Multi-Exposed-Images-with-Saturated-Regions
=========

Jun JIANG, Zhengguo LI, Shoulie XIE, Shiqian WU, and Liangcai ZENG <br>
Wuhan University of Science and Technology, Wuhan, 430081, China <br>
{jiangjun85, zengliangcai, shiqian.wu} @wust.edu.cn  <br>
Institute for Infocomm Research, Singapore, 138632 <br>
{ezgli, slxie}@i2r.a-star.edu.sg <br>

**Abstract:** It is challenging to align multi-exposed images due to large illumination variations, especially in presence of saturated regions. In this paper, a novel image alignment algorithm is proposed to cope with the multi-exposed images with saturated regions. Specifically, the multi-exposed images are first normalized by using intensity mapping functions (IMFs) in consideration of saturated pixels. Then, the normalized images are coded by using the local binary pattern (LBP). Finally, the coded images are aligned by formulating an optimization problem by using a differentiable-“Hamming”-distance. Experimental results show that the proposed algorithm outperforms state-of-the-art alignment methods for multi-exposed images in terms of alignment accuracy and robustness to exposure values.
# Challenges:

Multi-exposed images contain saturated regions, which yield huge differences among images.

LBP code does not capture the closeness of two bit-strings and it is sensitive to the rotation.

For binary descriptor, Hamming distance is non-differentiable and unsuitable for optimization

# The proposed method:

![](https://github.com/gelinlan/Robust-Alignment-of-Multi-Exposed-Images-with-Saturated-Regions/blob/master/Fig1.jpg) <br>
Fig.1 Flowchart of the proposed method. <br>

# Effects of intensity mapping functions (IMFs)
![](https://github.com/gelinlan/Robust-Alignment-of-Multi-Exposed-Images-with-Saturated-Regions/blob/master/Fig2.jpg) <br>
Fig.2 Effects of different IMFs. <br>
It can be observed that the images in (c) is more similar than (b), especially the clouds (in the middle) and the tree truck (in the right). Wu’s IMF is a unidirectional mapping function, which maps the image with more information to the one with less information to ensure two differently exposed images are consistent. However, the normalized results is not ideal due to large EV interval between two images. The proposed method employs a novel bi-directional mapping function. The intensities larger than ζ1 in the left image are unchanged, the remaining intensities in right images are mapped to left image to ensure the over-exposure region in both images are consistent. The intensities less than ζ2 in the right image remain constant, the remaining intensities in the left image are mapped to right image to ensure the under-exposure region in both images are consistent.

# Effects of feature descriptions
![](https://github.com/gelinlan/Robust-Alignment-of-Multi-Exposed-Images-with-Saturated-Regions/blob/master/Fig3.jpg) <br>
Fig.3 Effects of different feature map. <br>
It can be observed that, 8-bits-LBP coded images can represent more details of images. Two sets of 8-bits-LBP coded images with different exposure are more similar after normalization, such as the clouds and the tree trunk. 

# Effects of alignments
![](https://github.com/gelinlan/Robust-Alignment-of-Multi-Exposed-Images-with-Saturated-Regions/blob/master/Fig4.jpg) <br>
Fig.4 Aligned results. <br>
Hamming distance is used to match two sets 8 1-bit-string LBPs coded images shown in Fig4.(b). This method do not provide motion parameters but they provide the matching point pairs of two images. Thus, the performance of the Hamming distance is assessed by the number of consistent points and mismatching ones. Here, FSAT algorithm is used first to detect the feature points to reduce matching errors. However, the matched result is worse as shown in Fig.4(c), because it directly counts the number of mismatched bits, and can not be optimized. Conversely, the proposed method using a differentiable Hamming distance, which can be optimized to improve the align accuracy, as shown in Fig.4(d).

# Experimental Results
The proposed method is evaluated with a variety of synthesized images from benchmark datasets, public datasets（Cai's datasets [2] and real images. The proposed method are compared with: 1) existing non-parametric ordering features using MTB [3], CT [4], LBP [5] and BRIEF [6] methods, while employing the alignment algorithm shown in Section III; 2) the intensity-based IMF; 3) the feature-based method SIFT [7] and the hybird method IMF+SIFT; 4) IMF+BRIEF and IMF+BRIEF+“Hamming” distance (“HD”); 5) IMF+LBP [1]. 6) Learning-based matching methods SuperPoint [8] and LF-Net [9].
## Tests on synthesized sequences
To evaluate the robustness to exposure, the first image is selected as the reference and other images are rotated by 50, and shifted 30 pixels and 10 pixels in y-axis and x-axis respectively. Table1-2 are the motion errors on benchmark and public database. The average errors of the proposed method is the smallest, which implies the proposed method is suitable for various scene sets alignment and robust to intensity variations. Tables 3-6 summarize the motion errors on “Snowman”, “BigTree”, “Pillar” and “Inscription” sequences. 

TABLE 1. Overall results performed on benchmark database. 
![](https://github.com/gelinlan/Robust-Alignment-of-Multi-Exposed-Images-with-Saturated-Regions/blob/master/table1.jpg)

TABLE 2: Overall results performed on 37 Cai’s database
![](https://github.com/gelinlan/Robust-Alignment-of-Multi-Exposed-Images-with-Saturated-Regions/blob/master/table2.jpg)
![](https://github.com/gelinlan/Robust-Alignment-of-Multi-Exposed-Images-with-Saturated-Regions/blob/master/table3.jpg)
![](https://github.com/gelinlan/Robust-Alignment-of-Multi-Exposed-Images-with-Saturated-Regions/blob/master/table4.jpg)
![](https://github.com/gelinlan/Robust-Alignment-of-Multi-Exposed-Images-with-Saturated-Regions/blob/master/table5.jpg)
![](https://github.com/gelinlan/Robust-Alignment-of-Multi-Exposed-Images-with-Saturated-Regions/blob/master/table6.jpg)
![](https://github.com/gelinlan/Robust-Alignment-of-Multi-Exposed-Images-with-Saturated-Regions/blob/master/Fig5.jpg)
Fig.5 Comparison of IMF+LBP [1] , SuperPoint [8], LF-Net [9] and the proposed method on “BigTree” sequence (the first image and the last one). <br>
The learning-based methods, SuperPoint and LF-Net do not provide motion parameters but they provide the matching point pairs of two images. Thus, the performances of SuperPoint and LF-Net are assessed by the number of consistent points and mismatching ones. Comparing the two methods, SuperPoint finds only 1 pair of consist point as shown in Fig.5(a), which can not obtain the motion parameters between two images. By contrast, the method of LF-net can find more feature points, but can not match these feature points correctly, as shown in Fig.5(b). The performances of IMF+LP and the propose methods are estimated by the motion errors (shown in Tables 1-6), the performances of the two methods shown in Fig.5(c) and Fig.5(d), which direct overlay the two aligned images. It can observed that the proposed method is better than IMF+LBP, the result of IMF+LBP has ghosting and circled by the two red ellipses. 
## Tests on Real sequences
As motion parameters are unknown, the alignment results are evaluated in terms of mutual information (MI)[10], which is a successful measure for registering multi-modal images. Selecting the brightest image as reference, the MIs based on the 35 real sequences in file “Real sequences” are shown below.
It is noted that the MI values are different for various scenarios due to different contents (static/ dynamic scenes, little/severe saturation, and different EVs etc.), even the alignment performance is the same. But the performance comparison in terms of MI for the identical scene is meaningful.

![](https://github.com/gelinlan/Robust-Alignment-of-Multi-Exposed-Images-with-Saturated-Regions/blob/master/Fig6.jpg)
Fig.6 Mutual information for 35 real sequences.

## Tests on Efficiency
![](https://github.com/gelinlan/Robust-Alignment-of-Multi-Exposed-Images-with-Saturated-Regions/blob/master/table78.jpg)

# References
[1].	S. Q. Wu, Z. G. Li, J. H. Zheng, and Z. J. Zhu, “Exposure robust method for aligning differently exposed images,” IEEE Signal Processing Letters, vol. 21, no. 7, pp. 885–889, Jul. 2014. <br>
[2].	J. Cai, S. Gu, L. Zhang, “Learning a Deep Single Image Contrast Enhancer from Multi-Exposure Images,” IEEE Transactions on Image Processing, vol.27, no.4, pp.2049-2062. 2018. <br>
[3].	G. Ward, “Fast, robust image registration for compositing high dynamic range photographs from hand-held exposures,” Journal of graphics tools, vol.8, no.2, pp.17-30, 2003. <br>
[4].	R. Zabih and J. Woodfill, “Non-parametric local transforms for computing visual correspondence,” in Computer Vision-ECCV. Springer, pp.151-158, 1994. <br>
[5].	T. Ojala, M. Pietikainen, and D. Harwood “A comparative study of texture measures with classification based on featured distributions,” Pattern recognition, vol.29, no.1, pp.51-59, 1996. <br>
[6].	M. Calonder, V. Lepetit, M. Ozuvsal, T. Trzcinski, C. Strecha, and P. Fua, “BRIEF: Computing a local binary descriptor very fast,” IEEE Transactions on Pattern Analysis and Machine Intelligence, vol.34, no.7, pp.1281-1298, 2001. <br>
[7].	D. G. Lowe, “Distinctive Image Features from Scale-Invariant Keypoints,” International Journal of Computer Vision, vol.60, no.2, pp.91-110, 2004. <br>
[8].	D. DeTone, T. Malisiewicz, A. Rabinovich, “Superpoint: Self-supervised interest point detection and description,” 2017. <br>
[9].	Y. Ono, E. Trulls, P. Fua, and K. M. Yi, “Lf-net: Learning local features from images,” 2018. <br>
[10].	P. Viola, W. M. Wells, “Alignment by maximization of mutual information,”  Proceedings of IEEE International Conference on Computer Vision, vol. 24, no. 2, pp. 137-154, 1997. 
