---
layout:     post
title:      "marks "
subtitle:   " \"Reminder for paper readed\""
date:       2019-07-16 18:00:00 +0000
author:     "cy1c0n9"
header-img: "img/post-bg-2019.jpg"
tags:
    - fgv
---
- [End-to-End Real-Time ROI-Based Encryption in HEVC Videos](https://ieeexplore.ieee.org/abstract/document/8553038/figures#figures)
  - new codec, not easy to implement, drift in the result

- [Robust Encryption of Uncompressed Videos with a Selective Frame Scheme](https://ieeexplore.ieee.org/abstract/document/8529742)
  - S-DES + chaotic map + RSA to distribute key
  - takes too long to process video (likely one sec per frame)

- [An efficient privacy protection scheme for data security in video surveillance](https://www.sciencedirect.com/science/article/pii/S1047320319300367)
  - Silhouette-blur, de-identification, behaviour preservation, recoverable privacy content, and privacy protected video compression
  - on surveillance scenario, extract background, store the surveillance video data in a more secure fashion by breaking video into shares
  - <details>
<summary>lit review</summary>
<pre>
  For privacy protection algorithm, one category is “partial encryption” by scrambling, obscuring and blurring the sensitive region [25], [24], [23], [29]. Newton et al. [25] protected the privacy of individuals by directly substituting the faces with the averaging face. Chen et al. [24] removed the appearance information of the person by an obscuring algorithm. Tansuriyavong et al. [23] proposed a privacy protection system, in which the object is masked, revealing silhouette or name. However, these exposed information still allows identification. In such methods [25], [24], [23], the visual texture is discarded and the human behavior remains perceptible. However, these methods are mostly irreversible, and thus the privacy content cannot be recovered for future use. The other category is “complete encryption” [11], [12], [13], in which the video sequences are encrypted completely, such that zero visual information can be reconstructed. Privacy protection system [11] masked face in video sequences, which includes two modules: regions of interest (ROI) for face detection and JPEG 2000 encoding. However, the separation of ROI is with lower accuracy. Zhang et al. [12] stored privacy information in surveillance videos as a watermark, which can only be retrieved with a secret key. However, the watermarking and encryption are with high computational cost. Furthermore, Dufaux et al. [13] proposed an efficient solution via ROI transform-domain scrambling, in which the signs of selected coefficients is flipped during encoding. Secure Shape and Texture SPIHT (SecST-SPIHT) coding scheme [14] encrypted visual objects for privacy protection. The content is only available to authorized users with the decryption key. Martin et al. [15] proposed a system for providing privacy in a distributed way using threshold multi-party computation, which provides a certain degree of protection against operator misuse. However, the encryption process also impedes human behavior analysis.
  </pre>
  </details>

- [A Lightweight Encryption Method for Privacy Protection in Surveillance Videos](https://ieeexplore.ieee.org/stamp/stamp.jsp?tp=&arnumber=8329515)
  - using Layered CA to encrypt/decrypt ROI
  - but set the original ROI to white, and store the encrypted ROI separately
  - is it possible not to use extra storage?
