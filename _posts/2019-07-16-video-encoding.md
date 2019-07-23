---
layout:     post
title:      "Lit review on how to encrypt ROI in video"
subtitle:   " \"Reminder for paper readed\""
date:       2019-07-16 18:00:00 +0000
author:     "cy1c0n9"
header-img: "img/post-bg-2019.jpg"
tags:
    - fgv
---

- [Chaos-based selective encryption for H.264/AVC](https://www.sciencedirect.com/science/article/pii/S0164121213001994) Rank A
    - <details><summary>complete encryption and selective encryption</summary><pre>For complete or full encryption, all the data in the video
    stream are encrypted. In Fan et al. (2007), a number of cryptographic
    algorithms are employed to encrypt different parts of the video
    stream so that all the contents are completely encrypted. However,
    its computational complexity is too heavy to satisfy the real-time
    requirement.
    In partial or selective encryption algorithms, only the important
    data are encrypted to reduce the computational complexity for
    achieving a near real-time performance (Wang et al., 2007). There
    are already a number of selective encryption algorithms working on
    different video parameters. Some of them are specially designed
    for the H.264 standard, for example, encrypt the signs of DCT
    coefficients or the motion vectors (Tong et al., 2010, Park and
    Shin, 2008), hash the DCT coefficients (Zhang et al., 2009,
    Wang et al., 2010) and scramble the intra prediction mode (Jiang
    et al., 2009, Su et al., 2011), etc. The goal of performing selective
    encryption is to save the computation time at adequate security.
    Moreover, there is a special type of selective encryption which
    belongs to perceptual encryption. The aims of this kind of encryption
    are mainly to destroy the commercial value of the video clips to
    prevent the abuse or immoral use of them (Liu and Koenig, 2010).
    However, the classification and the difference between perceptual
    encryption and selective encryption are not clearly defined in
    most of the existing algorithms (Spinsante et al., 2005, Thomas
    et al., 2007). Therefore, in the rest of this paper, we will use
    the term selective encryption for simplicity.
    - security of chaos system
    - but this paper is proposed for encrypted whole video

-  &#9745; [An ROI Privacy Protection Scheme for H.264 Video Based on FMO and Chaos](https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=6507633) (IEEE Transactions on Information Forensics and Security) Rank A
    - talked about chaos theory, can be used for final report

- &#9745; [H.264/AVC video scrambling for privacy protection](https://ieeexplore.ieee.org/abstract/document/4712098) (ICIP) Rank B
    - too old...
    - 2008

- &#9745; [A Lightweight Encryption Method for Privacy Protection in Surveillance Videos](https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=8329515) Rank B
    - using Layered CA to encrypt/decrypt ROI
    - but set the original ROI to white, and store the encrypted ROI separately
    - is it possible not to use extra storage? No
    - key challenge is to store the face frames efficiently

- [A framework for the validation of privacy protection solutions in video surveillance](https://ieeexplore.ieee.org/abstract/document/5583552) ICME (Rank B)
    - 2010

- [Restricted H.264/AVC video coding for privacy region scrambling](https://ieeexplore.ieee.org/abstract/document/5653444) ICIP Rank B
    -
- [Privacy region protection for H.264/AVC by encrypting the intra prediction modes without drift error in I frames](https://ieeexplore.ieee.org/abstract/document/6638201) ICASSP Rank B

- pixels level permutation:
    - &#9745; [A real-time privacy-sensitive data hiding approach based on chaos cryptography](https://ieeexplore.ieee.org/abstract/document/5583558) (B) (2010)
    - [Two Level Image Encryption using Pseudo Random Number Generators](https://pdfs.semanticscholar.org/5ce3/c6bb2753db29f6a3a9a48820565f5f714ace.pdf)(C),
    - [Compression Independent Reversible Encryption for Privacy in Video Surveillance](https://core.ac.uk/download/pdf/81554775.pdf)(not found)
    - [Evaluating the permutation and diffusion operations used in image encryption based on chaotic maps](http://faratarjome.ir/u/media/shopping_files/store-EN-1484733335-8924.pdf) (take times(almost 1 sec) to encrypt an image)(not found)

- [End-to-End Real-Time ROI-Based Encryption in HEVC Videos](https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=8553038) (EUSIPCO) Rank B
- [ROI encryption for the HEVC coded video contents](https://ieeexplore.ieee.org/abstract/document/7351373) (ICIP) Rank B
    - The encode block is too large as shown on the paper, new codec

- Selective encryption != ROI encryption !!!
    - Here is one of [selective encryption algorithms](https://www.sciencedirect.com/science/article/pii/S0030402616307859)
    - Selective encryption work on the whole video domain, which encrypt selective parameters in  like several coefficients like IPM / signs of T1s / signs of non-zero
    - which is not what we need

- [Robust Encryption of Uncompressed Videos with a Selective Frame Scheme](https://ieeexplore.ieee.org/abstract/document/8529742) International Conference for Convergence in Technology Rank C
    - S-DES + chaotic map + RSA to distribute key
    - takes too long to process video (likely one sec per frame)

- [An efficient privacy protection scheme for data security in video surveillance](https://www.sciencedirect.com/science/article/pii/S1047320319300367)
    - Silhouette-blur, de-identification, behaviour preservation, recoverable privacy content, and privacy protected video compression
    - on surveillance scenario, extract background, store the surveillance video data in a more secure fashion by breaking video into shares
    - <details><summary>lit review</summary><pre>For privacy protection algorithm, one category is “partial encryption” by scrambling, obscuring and blurring the sensitive region [25], [24], [23], [29].
    Newton et al. [25] protected the privacy of individuals by directly substituting the faces with the averaging face.
    Chen et al. [24] removed the appearance information of the person by an obscuring algorithm.
    Tansuriyavong et al. [23] proposed a privacy protection system, in which the object is masked, revealing silhouette or name.
    However, these exposed information still allows identification.
    In such methods [25], [24], [23], the visual texture is discarded and the human behavior remains perceptible.
    However, these methods are mostly irreversible, and thus the privacy content cannot be recovered for future use.
    The other category is “complete encryption” [11], [12], [13], in which the video sequences are encrypted completely, such that zero visual information can be reconstructed.
    Privacy protection system [11] masked face in video sequences, which includes two modules: regions of interest (ROI) for face detection and JPEG 2000 encoding.
    However, the separation of ROI is with lower accuracy.
    Zhang et al. [12] stored privacy information in surveillance videos as a watermark, which can only be retrieved with a secret key.
    However, the watermarking and encryption are with high computational cost.
    Furthermore, Dufaux et al. [13] proposed an efficient solution via ROI transform-domain scrambling, in which the signs of selected coefficients is flipped during encoding.
    Secure Shape and Texture SPIHT (SecST-SPIHT) coding scheme [14] encrypted visual objects for privacy protection.
    The content is only available to authorized users with the decryption key.
    Martin et al. [15] proposed a system for providing privacy in a distributed way using threshold multi-party computation, which provides a certain degree of protection against operator misuse.
    However, the encryption process also impedes human behavior analysis.


- [Secure and Fast Chaos based Encryption System using Digital Logic Circuit](https://pdfs.semanticscholar.org/88ba/3ecfcae3d8956123b48c657797de7fa864ea.pdf) Rank C

- [Lossless ROI Privacy Protection of H.264/AVC Compressed Surveillance Videos](https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=7181657) jurnal not found in Core, but [here](https://www.scimagojr.com/journalsearch.php?q=21100338508&tip=sid&clean=0) and [here](https://www.letpub.com/index.php?journalid=10210&page=journalapp&view=detail)
    - trying to fix the problem of pixel-drift in non-privacy pixels
    - It is mentioned that pixel-domain approaches reduce the video compression efficiency, and it is impossible to recover the original compressed video sequences. (the recovered video will be lossy, but i think it is fine in those pixel-domain solution)
    - <details><summary>CAVLC</summary><pre>CAVLC: quantized transform coefficient it is an inherently lossless compression technique, like almost all entropy-coders.
    - XORing several bits like AC coefficients and IPMDs
    - Then refresh the blocks around the privacy regions

- [Secure JPEG scrambling enabling privacy in photo sharing](https://ieeexplore.ieee.org/abstract/document/7285022) (FG) Rank C
    - works on JPEG image, but not likely to work on video domain (different encode format)

- [Fully Reversible Privacy Region Protection for Cloud Video Surveillance](https://ieeexplore.ieee.org/abstract/document/7208839) journal not found, but seems not a good transaction
    - extension for lossless = =
    - "To our best knowledge, the proposed scheme is the first fully reversible one for privacy region protection"

- [A Coprime Blur Scheme for Data Security in Video Surveillance](https://ieeexplore.ieee.org/abstract/document/6585237)
    - not useful in our case
    - divide into two streams, that can be integrate into one streams

- can we relax down the requirement that the server check whether the user is permitted to view and encrypt the forbidden part? encryption can be done in a fast manner.

- <details><summary>Lorenz</summary><pre>
    开发的算法中遵循的步骤是图式化的,图10.1和详细说明如下：
    1.Lorenz吸引子分为两个主子系统和子系统，我们用它作为同步变量ay，因为它的Lyapunov指数是最负的
    （它们越负，它们就越快）。它会收敛）。
    2.使用接近吸引子区域的随机初始条件初始化子系统。
    3.吸引器同步将主组件发送到从属设备。使用Runge Kutta 4生成主吸引子的前2500个值，跳跃h = 0.01
    （百分之一秒），并将结果作为公钥k发送给从属吸引器。
    4.视频帧每0.03秒拍摄一次。
    它被认为是长度为mXn的帧I.从应用于Lorenz吸引子的Runge Kutta 4开始，构建长度为m×n的序列Sc，
    从迭代2501开始。序列Sc的前m + n值将用于该过程。置换，而以下n值将用于扩散过程。
    要交换行，使用在Sc序列的x分量中获得的前m个值，其中每个值指示行的每个像素必须以圆形方式朝向的方向
    移动的位置的数量如果值x为正，则为右，如果为负，则为左。随后，序列Sc的x分量的以下n个值用于指示如果
    继承的值，则帧的每列像素应当以向下的圆形方式向下移动的位置的数量。在为负的情况下为正或向上，获得置
    换矩阵P.在数学上，每个像素的位移由公式10.1给出
    在S对应于序列Sc的位置i的分量x的情况下，这种类型的位移被称为圆形，因为整个行或列的像素被移位一定数
    量的位置并且如果从最后一个位置经过，则从行或列的第一个位置开始计数。为简单起见，该过程的结果由perm
    表示，在等式10.2中给出。
    对于扩散过程，通过序列Sc从2501到2501 + m获得的第一个值用于生成列向量并重复n次，直到构建扩散矩阵D.
    置换帧P的值与扩散矩阵D进行矢量求和。加密帧C对应于等式10.3。对于生成视频加密的每个帧重复前面的步骤。
    值得一提的是，为了检索信息，必须执行上述过程，但是以相反的方式，也就是说，扩散过程将开始，因为它是
    最后执行的过程。如果进行扩散以进行扩散，则为了恢复信息，必须进行减法，一旦完成上述操作，将在发送时
    再次获得多媒体内容。
    结果：
    第一阶段的工作包括借用阴极动力系统理论的概念基础以及将天主教吸引子纳入密码学的方法，另外使用作为同
    步属性。利用参考文献[7,8,11,12,13,14,15,16,17,18,19,20,21,22,23,24]中所示技术的优势，并考
    虑实时传输视频，提出了一种基于Lorenz吸引子和同步原理的技术，可以在不浪费时间发送密钥的情况下对帧进
    行加密，实现这一目的单个密钥，称为同步密钥，在发送方和接收方之间共享，其安全性取决于发送信道，用于
    使接收吸引器与发送吸引器同步。为了实现所提出的算法，选择了Python语言的CV2库，这允许容易地操纵由摄
    像机捕获的帧。进行了不同的性能和安全测试，重点是排列和扩散过程应该采取的顺序。进行了三次安全测试，
    第一次只是扩散，注意到图11.1a的原始框架的某些轮廓是可见的，如图11.1b所示。在第二次测试中，仅使用
    排列，框架完全失去其原始外观，如图11.1c所示。在第三个测试中，使用了两个扩散和置换过程，观察到如果
    首先应用置换然后扩散，那么相关性虽然很小，但仍然存在（图11.1d），但是首先实现扩散和排列（图11.1e）
    ，实现了更好的指标和对算法性能的不可察觉的影响。
    The analysis of key space is important to evaluate the security of the algorithm
    in case an intruder tries to perform a brute force attack, trying to hit the
    synchronization key by iteration. Calculating the initial key space (2500 values)
    implies considering the limits for the Lorenz cathic attractor (from -10 to 10
    for the coordinate in x, from -15 to 15 in the coordinate, and from 0 to 40 in the
    coordinate), and the unit of time considered for the attractor of 0.01, so for each
    interval of only one unit, for example from -10.00 to -9.00 there are 100 values,
    only with the component in x will be generated. There are 2000 numbers, which
    results in possible combinations to obtain a point of coordinates, if one also
    takes into account that the length of the key is 2500, the key space turns out
    to be. It is valid to point out that this key space is exponential insofar as
    the unit of time is reduced.
    The UACI (Unified Average Changing Intensity) and NPCR (Number of Pixels Change
    Rate) metrics are based on the impact that can be caused by the change of a
    single pixel of an encrypted frame, commonly used by attackers to recognize a
    pattern on the frames thrown by the encryption algorithms. The NPCR is the pixel
    change rate and measures the percentage of different pixels between two frames,
    while the UACI is the unified average of change intensity and measures in
    percentage the difference between two frames. The expressions for NPCR and UACI
    are given by equations 12.1 and 12.2.
    where M and N represent respectively the width and height of the frame. C1, C2,
    denote two frames with a single difference pixel D (i.j) = 0, if C1 (i.j) = C2 (i.j)
    and 1 otherwise. It is considered that the closer the UACI is to 33.4635% and
    the NP CR to 99.6094% greater is the security offered by the algorithm. The
    results for the algorithm developed in this work were on average 37.2395833333%
    and 99.6327% for the UACI and the NP CR respectively.

    - key space?


Bit-stream domain approaches modify the compressed information (such as the DCT coefficients, intra-frame prediction modes and motion vector differences) in the bit-stream domain based on traditional encryption such as chaos stream cipher [6]
