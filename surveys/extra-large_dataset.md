# 超大规模数据集（TB级别以上）调研

本调研总结了TB级别以上数据集的简单说明与地址，不限数据类型。其中包含了一些压缩后不足1TB的数据集，他们的原始文件大小均为1TB以上.

## 文本数据

- CC-100：大规模CommonCrawl`文本数据集`，包括100种语言(用于训练XLM-R)的`2.5TB`干净的无监督文本语料；
  + download and paper: http://data.statmt.org/cc-100/
  + institution: Facebook AI

- 互联网语料库(SogouT)：来自互联网各种类型的1.3亿个原始网页, 压缩前的大小超过了`5TB`
  + download: http://www.sogou.com/labs/resource/t.php
  + institution: Sogou Lab

- AWS爬虫数据：收集了从2008以来抓取的50亿个网页的数据。其中自2013年开始，所有爬虫只持续一个月，数据以WARC文件格式存储。
从2012年开始，抓取的数据还包含元数据（WAT）和文本数据（WET）提取，大大简化了数据处理，大小约`541 TB`
  + download: https://registry.opendata.aws/commoncrawl/
  + institution: Amazon AWS

- Google Books Ngrams：包含在整个语料库中出现超过40次的n-gram，优化了快速查询小组短语的用法，`2.2TB`
  + download：http://storage.googleapis.com/books/ngrams/books/datasetsv2.html
  + institution: Google

- 1.7 billion comments on Reddit: The dataset is ~1.7 billion JSON objects complete with the comment, score,
author, subreddit, position in comment tree and other fields that are available through Reddit's API. 
This dataset is over `1 terabyte` uncompressed.
  + download: https://www.reddit.com/r/datasets/comments/3bxlg7/i_have_every_publicly_available_reddit_comment/


## 视频/图像数据

- YouTube-8M: A Large-Scale Video Classification Benchmark. 包含三个级别的视频数据及其标注：
Segment-rated frame-level features dataset, Frame-level features dataset (`1.53TB`), Video-level features dataset (`31GB`)
  + download: http://research.google.com/youtube8m/download.html
  + paper: YouTube-8M: A Large-Scale Video Classification Benchmark (https://arxiv.org/abs/1609.08675)
  + institution: Google

- StarCraft: Brood War replay dataset yet, with 65646 games. The full dataset `after compression` is `365 GB`, 
1535 million frames, and 496 million player actions. The entire frame data was dumped out at 8 frames per second.
  + download: https://github.com/TorchCraft/StarData
  + paper: https://arxiv.org/abs/1708.02139
  + institution: Facebook AI

- 自动驾驶数据集: 这些数据涵盖了Waymo在收集的多种环境信息，包括白天与黑夜、黄昏和黎明、阳光和雨天，涵盖了城市中心和郊区。数据集大小约为`1.35TB`
  + download: https://waymo.com/open
  + institution: Waymo

- 大规模 Deepfake 数据集 DFDC：3426 名对象，每个对象平均录制 14.4 个视频，大部分视频的分辨率为1080p；48,190 个视频，
每个视频的平均长度为 68.8秒，共计长度 38.4天；原始数据超过`25TB`。
  + download: https://www.kaggle.com/c/deepfake-detection-challenge/data
  + institution: Facebook AI

- Open Images Dataset: Open Images is a dataset of ~9 million URLs to images that have been annotated with labels
spanning over 6000 categories, `561GB after compressed, 18TB uncompressed`.
  + download: https://github.com/cvdfoundation/open-images-dataset#download-images-with-bounding-boxes-annotations

## 其他数据集

这些数据集无法准确的列出大小或下载地址，但都是公开的数据集，其大小参考了一些已发表论文中的描述

- Sloan Digital Sky Survey (SDSS) dataset: one of the largest astronomical catalogs publicly accessible (`more than 3.4TB`).
  + download: https://www.sdss.org/dr13/
  + paper: *Dawson, K. S., Kneib, J. P., Percival, W. J., Alam, S., Albareti, F. D., Anderson, S. F., ... & Zou, H. (2016). The SDSS-IV extended Baryon Oscillation Spectroscopic Survey: overview and early data. The Astronomical Journal, 151(2), 44.*
  + find this dataset in: *Yan, Y., Cao, L., Kulhman, C., & Rundensteiner, E. (2017, August). Distributed local outlier detection in big data. In Proceedings of the 23rd ACM SIGKDD international conference on knowledge discovery and data mining (pp. 1225-1234).*


