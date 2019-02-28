# ICDAR 2019 Robust Reading Challenge on Scanned Receipts OCR and Information Extraction
## Introduction
Scanned receipts OCR is a process of recognizing text from scanned structured and semi-structured receipts, and invoices in general. On the other hand, extracting key texts from receipts and invoices and save the texts to structured documents can serve many applications and services, such as efficient archiving, fast indexing and document analytics. Scanned receipts OCR and information extraction (SROIE) play critical roles in streamlining document-intensive processes and office automation in many financial, accounting and taxation areas. However, SROIE also faces big challenges. With performance greatly boosted by recent breakthroughs in deep learning technologies in terms of accuracy and processing speed, OCR is becoming mature for many practical tasks (such as name card recognition, license plate recognition and hand-written text recognition). However, receipts OCR has much higher accuracy requirements than the general OCR tasks for many commercial applications. And SROIE becomes more challenging when the scanned receipts have low quality. Therefore, in the existing SROIE systems, human resources are still heavily used in SROIE. There is an urgent need to research and develop fast, efficient and robust SROIE systems to reduce and even eliminate manual work.<br />
With the trends of OCR systems going to be more intelligent and document analytics, SROIE holds unprecedented potentials and opportunities, which attracted huge interests from big companies, such as Google, Baidu and Alibaba. Surprisingly, there are little research works published in the topic of SROIE. While robust reading, document layout analysis and named entity recognition are relevant to the SROIE, none of the existing research and past ICDAR competitions fully address the problems faced by SROIE [1,2,3].<br />
In recognition of the above challenges, importance and huge commercial potentials of SROIE, we propose the ICDAR 2019 competition on SROIE, aiming to draw attention from the community and promote research and development efforts on SROIE. The proposed competition could be of interests to the ICDAR community from several aspects:
* To support the competition, a large-scale and well-annotated invoice datasets are provided, which is crucial to the success of deep learning based OCR systems. While many datasets have been collected for OCR research and competitions, to the best of our knowledge, there is no publicly available receipt dataset. Compared to the existing ICDAR and other OCR datasets, the new dataset has some special features and challenges, e.g., some receipts having poor paper quality, poor ink and printing quality; low resolution scanner and scanning distortion; folded invoices; too many unneeded interfering texts in complex layouts; long texts and small font sizes. To address the potential privacy issue, some sensitive fields (such as name, address and contact number etc) of the receipts are blurred. The datasets can be an excellent complement to the existing ICDAR and other OCR datasets.
* Two specific tasks are proposed: **receipt OCR** and **key information extraction**. Compared to the other widely studied OCR tasks for ICDAR, receipt OCR (including text detection and recognition) is a much less studied problem and has some unique challenges. On the other hand, research works on extraction of key information from receipts have been rarely published. The traditional approaches used in the named entity recognition research are not directly applicable to the second task of SROIE.
* Comprehensive evaluation method is developed for the two competition tasks. In combination with the new receipt datasets, it enables wide development, evaluation and enhancement of OCR and information extraction technologies for SROIE. It will help attract interests on SROIE, inspire new insights, ideas and approaches.
## Tasks
### Task 1 - Scanned Receipt OCR
#### Task Description
Localizing and recognizing text are conventional tasks that has appeared in many previous competitions, such as the ICDAR Robust Reading Competition (RRC) 2013, ICDAR RRC 2015 and ICDAR RRC 2017 [1][2]. The aim of this task is to accurately localize texts with 4 vertices and recognize the text in the localized bounding boxes. The text localization ground truth will be at least in the level of words. Participants will be asked to submit a zip file containing results for all test images.
#### Evaluation Protocol
As participating teams may apply localization algorithms to locate text at different levels (e.g. text lines), for the evaluation of text localizazation in this task, the methodology based on DetVal will be implemented. The methodology will address the problem of one-to-many and many to one correspondences of detected texts. In our evaluation protocol mean average precision (mAP) and average recall will be calculated, based on which F1 score will be computed and used for ranking [3]. A detected text is marked as true positive if 1) IoU with ground truth box(es) is larger than a given threshold; 2) the ground truth box has not been matched to another detection yet; and 3) the recognized text in the detected box matches the ground truth text.
### Task 2 - Key Information Extraction from Scanned Receipts
#### Task Description
The aim of this task is to extract texts of a number of key fields from given receipts, and save the texts for each receipt image in a json file with format shown in Figure 3. Participants will be asked to submit a zip file containing results for all test invoice images.
#### Evaluation Protocol
For each test receipt image, the extracted text is compared to the ground truth. An extract text is marked as correct if both submitted content and category of the extracted text matches the groundtruth; Otherwise, marked as incorrect. The mAP is computed over all the extracted texts of all the test receipt images. F1 scored is computed based on mAP and recall. F1 score is used for ranking.
## Dataset and Download
The dataset will have 1000 whole scanned receipt images. Each receipt image contains around about four key text fields, such as goods name, unit price and total cost, etc. The text annotated in the dataset mainly consists of digits and English characters. An example scanned receipt is shown below:<br />
![image](https://github.com/SYZNKJ2019/SORIE2019/blob/master/sample21.png)<br />
The dataset is split into a training/validation set (“trainval”) and a test set (“test”). The “trainval” set consists of 600 receipt images which will be made available to the participants along with their annotations. The “test” set consists of 400 images, which will be made available a few weeks before the submission deadline.<br />
For receipt OCR task, each image in the dataset is annotated with text bounding boxes (bbox) and the transcript of each text bbox. Locations are annotated as rectangles with four vertices, which are in clockwise order starting from the top. Annotations for an image are stored in a text file with the same file name. The annotation format is similar to that of ICDAR2015 dataset, which is shown below:<br />
x1_1, y1_1,x2_1,y2_1,x3_1,y3_1,x4_1,y4_1, transcript_1<br />
x1_2,y1_2,x2_2,y2_2,x3_2,y3_2,x4_2,y4_2, transcript_2<br />
x1_3,y1_3,x2_3,y2_3,x3_3,y3_3,x4_3,y4_3, transcript_3<br />
…<br />
For the information extraction task, each image in the dataset is annotated with a json file with format shown below:<br />
{"Vt Pep Mocha": "4.95",<br />
"Total": "$4.95",<br />
"date": "14/03/2015",<br />
   ……………<br />
}<br />
Click [Baidu Netdisk ](http://rrc.cvc.uab.es/?ch=13&com=downloads) or [Google Drive](http://rrc.cvc.uab.es/?ch=13&com=downloads)to download dataset.
## Timeline
**Registration open**: February 10 – March 31, 2019<br />
**Training/validation dataset available**: March 1, 2019<br />
**Submission open**: April 15, 2019<br />
**Deadline for Competition participants**: April 30, 2019<br />
## Organizers
<font color="#0000dd">**SROIE Challenge Organization Team**</font><br />
* **Dr Zheng Huang** (huang-zheng@sjtu.edu.cn), Shanghai Jiaotong University, China<br />
* **Dr Kai Chen** (kaichen@onlyou.com), Onlyou, China<br />
* **Dr Jianhua He** (j.he7@aston.ac.uk), Aston University, UK<br />
* **Dr Xiang Bai** (xbai@hust.edu.cn), Huazhong University of Science and Technology, China<br />
* **Dr Dimosthenis Karatzas** (dimos@cvc.uab.es), Universitat Autónoma de Barcelona, Spain<br />
* **Dr Shijian Lu** (Shijian.Lu@ntu.edu.sg), Nanyang Technological University, Singapore<br />
* **Dr C. V. Jawahar** (jawahar@iiit.ac.in), IIIT Hyderabad, India<br />
## References
[1]. D. Karatzas, F. Shafait, S. Uchida, M. Iwamura, L. Gomez, S. Robles, J. Mas, D. Fernandez, J. Almazan, L.P. de las Heras: ICDAR 2013 Robust Reading Competition. ICDAR, 2013.<br />
[2]. D. Karatzas, L. Gomez-Bigorda, A. Nicolaou, D. Ghosh , A. Bagdanov, M. Iwamura, J. Matas, L. Neumann, VR. Chandrasekhar, S. Lu, F. Shafait, S. Uchida, E. Valveny: ICDAR 2015 robust reading competition. ICDAR, 2015.<br />
[3]. Everingham, M. and Eslami, S. M. A. and Van Gool, L. and Williams, C. K. I. and Winn, J. and Zisserman, A.: The Pascal Visual Object Classes Challenge: A Retrospective. IJCV, 2015.<br />
[4]. D. Karatzas, L. Rushinol, The Robust Reading Competition Annotation and Evaluation Platform.
