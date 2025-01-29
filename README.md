# Instance segmentation of fashion images with Mask R-CNN
งานหลัก ๆ ในทาง **Computer Vision** เราสามารถแบ่งออกได้เป็นสี่อย่าง ได้แก่ Classification ,Semantic Segmentation, Object Detection และ Instance Segmentation สำหรับโปรเจคนี้ของเราเป็นการทํา Instance Segmentation กับงานด้านแฟชัน ด้วย Mask R-CNN คือการหาว่าวัตถุต่างๆ ภายในรูปมี pixel ใดบ้าง ซึ่ง Mask R-CNN คือโมเดลที่ออกแบบมาเพื่อใช้สำหรับงานนี้โดยเฉพาะ

<p align="center"><img width="700" src = "https://github.com/user-attachments/assets/3bef35d6-e953-48c7-a0d6-b56e8a7a41ac"/></p>
<p align="center" >
  <a href="#Introduction-and-Objectives">Introduction and Objectives</a> •
  <a href="#getting-started">Getting Started</a> •
  <a href="#Methods-and-Materials">Methods and Materials</a> •
  <a href="#Results">Results</a> 
</p>

## Introduction and Objectives
Clothing and accessories account for over 25% of total e-commerce revenue, making their categorization using computer vision a compelling topic. Fashion image analysis has gained popularity due to its commercial and cultural significance. Computer vision in fashion not only recognizes image features but also interprets their combinations.

However, real-world applications remain challenging due to the complex shapes and diverse appearances of fashion items, which can introduce inaccuracies. The goal of object detection and segmentation is to achieve precise pixel-level separation, enhancing accuracy in fashion image analysis.

## Getting Started
To run this app on jupyter notebook or Google Colab, follow these steps:
1. Clone this repository to your local machine using `git clone https://github.com/mmaitty01/Instance-Segmentation_MaskRCNN.git`
2. Open the project in jupyter notebook or Google Colab.
3. run the project.

## Methods and Materials
โมเดล Mask-CNN ที่ใช้ในการประมวลผลได้ มีการประมวลผลโดย ใช้ GPU บนเครื่องคอมพิวเตอร์ระบบปฏิบัติการ Windows10
1. **Import and Define**
- ขั้นแรกเป็นการ Import ตัว Library ต่างๆ และกําหนดค่าตัวแปรที่ต้องใช้
2. **Download Libraries and Pretrained Weights**
- ได้เลือก Mask R-CNN ของบริษัท Matterport มาใช้ โดยทําการดาวน์โหลด Library  รวมทั้งดาวน์โหลด Pretrained Weight ที่มีให้ด้วย
3. **Set Config**
- โมเดล Mask R-CNN จะมี Hyperparameter ให้ปรับได้มาก ในที่นี้ได้ทําการปรับแค่บ้างตัว เพื่อลดเวลาในเทรน
4. **Prepare Datasets**
- การอ่าน Dataset โดยเริ่มจากไฟล์ label_descriptions.json ซึ่งบอกข้อมูลของ Label โดยเราจะเก็บชื่อของ Category ไว้ใช้อ้างอิงและแสดงผล มีการเพิ่ม Category ของประเภทรองเท้า ได้แก่ Canvasshoes, High-Heels และ Sandals 
5. **Visualization**
- ก่อนที่จะเทรน ก็จะทําการแบ่งข่อมูลเป็น Training Set กับ Validation Set เมื่อสร้าง Training Set และ Validation Set เสร็จแล้วก็จะลองทํา Visualization ดูว่า Category ต่างๆ มีการกระจายเป็นอย่างไรบ้าง
6. **Train**
- ในขั้นแรกของกระบวนการเทรน ก็จะสร้างโมเดล Mask R-CNN จาก Config ที่กําหนดไว้ และโหลด Pretrained Weight มาใส่
7. **Predict**
- ขั้นตอนสุดท้ายก็จะเป็นการนําโมเดลที่เทรนไว้มาใช้ทํานาย Test Data โดยเริ่มจากการเซ็ตค่า Config แล้วโหลดโมเดลที่เทรนไว้ขึ้นมา

## Results
เมื่อสร้างคลาส Dataset ของข้อมูลชุดนี้สําเร็จ ก็จะสามารถลองทํา Visualization ดูได้ว่ามีรูปภาพและ Mask เป็นอย่างไรบ้าง โดย Mask Head จะแสดง Class ของชิ้นส่วนเสื้อผ้าที่ทํานายคู่กับค่า IoU ซึ่งมีค่าเข้าใกล้ 1 เมื่อ Pixel ค่าทํานายเท่ากับ Pixel ของชิ้นส่วนเสื้อผ้านั้นๆใน train data ซึ่งแสดงความน่าเชื่อถือของ Class ที่ทํานาย 

<p align="center"><img width="600" src = "https://github.com/user-attachments/assets/32ffe41b-98af-4105-ab9d-2a0fc468d76e"></p>
<p align="center"><img width="250" height = "380" src = "https://github.com/user-attachments/assets/29852b36-44d1-40b9-a9cc-50abdc1b1c0f">
<img width="250" height = "380"  src = "https://github.com/user-attachments/assets/62d861cc-dda8-449d-b68c-6d27b47480f1">
<img width="250" height = "380"  src = "https://github.com/user-attachments/assets/ed16342c-5537-48e6-bbf1-6e59893cd476"></p>
