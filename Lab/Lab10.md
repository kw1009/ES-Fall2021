# Lab10 AI最經典火紅的應用之人臉偵測實作

#### 目錄
<a name="000"/>

##### [10-1 虛擬人臉數據](#001)
##### [10-2 OpenCV電腦視覺](#002)
##### [10-3 人臉辨識](#003)

<a name="001"/>

## Lab 10-1 虛擬人臉數據取得

![螢幕擷取畫面 2021-12-05 102733](https://user-images.githubusercontent.com/89327102/145698517-43420aa6-738a-4c3f-bbc9-4cdd56282374.jpg)

````c

# 000
print('hello AI')

"""##記得要使用GPU (編輯 >> 筆記本設定 >> GPU)"""

# 001 將我們的Google Drive連結上Virtual Machine
from google.colab import drive
drive.mount('/content/drive')

# 002 Check the current working directory
!pwd

# Commented out IPython magic to ensure Python compatibility.
# 003 Change the right working directory

%cd '/content/drive/MyDrive/ES2021/exp_FD_20211205'

# 004 Check again
!pwd

"""## Topic 1: 人臉數據取得"""

#101 虛擬人造人臉
from IPython.display import Image
print('這都是虛擬人造人臉')
Image('face31.jpg',width=400)

"""## Lab 1"""

"""### Lab1: 讓我們下載2張自選的虛擬人造臉 (VF04.jpg, VF05.jpg), 並且上傳到我們的Google Drive, 並且用以上的指令來顯示出來"""
#102 Lab: 自行下載二張來試試 face generator, https://thispersondoesnotexist.com/

#虛擬人造人臉1
Image('VF04.jpg',width=200)

# 103 虛擬人造人臉2
Image('VF05.jpg',width=200)

````

<a name="002"/>

## Lab 10-2 OpenCV電腦視覺入門

![螢幕擷取畫面 2021-12-05 102800](https://user-images.githubusercontent.com/89327102/145698537-812a3983-8a86-46c0-b999-83a340adeca2.jpg)

````c

"""## Topic 2: OpenCV`電腦視覺`入門"""

# Commented out IPython magic to ensure Python compatibility.
#201 讀取黑白圖片

# %matplotlib inline
import matplotlib.pyplot as plt
import cv2
cv2.__version__ #版本不斷更新中

#顯示圖片
import numpy as np
img=cv2.imread('face31.jpg',0) #0 grayscale 1 color
from google.colab.patches import cv2_imshow
cv2_imshow(img) # correct method

#202 讀取彩色圖片
img=cv2.imread('face31.jpg',1)
cv2_imshow(img)
img.shape

#203 openCV是 BGR
import matplotlib.pyplot as plt
img = cv2.imread("face31.jpg") # 圖片讀取到img變數
#plt.figure(figsize=(4,3))
#plt.axis("off") 
plt.imshow(img) # 圖片顯示

#204 BGR to RGB

img1=cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
plt.imshow(img1)

#205 openCV簡易繪圖範例
import numpy as np
# 建立一張 256x256 的 RGB 圖片（0黑色）
img = np.zeros((256, 256, 3), np.uint8) #np.zeros建立0矩陣
# 將圖片用淺灰色 (200, 200, 200) 填滿
img.fill(200)
# 在圖片上畫一條紫紅色的對角線，寬度為 5 px (0,0在最左上角)
# cv2.line(影像, 開始座標, 結束座標, 顏色, 線條寬度)
cv2.line(img, (0, 0), (255, 255), (255, 0, 255), 5)
# 顯示圖片
cv2_imshow(img)


'''#206: 在圖片上畫二條交錯的紫紅色的對角線，寬度為 5 px (0,0在最左上角), '''

# Your Code

````
## Lab 10-3 人臉辨識實際應用
