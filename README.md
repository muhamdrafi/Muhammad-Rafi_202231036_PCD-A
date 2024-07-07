# Muhammad-Rafi_202231036_PCD-A

-import library
```python
import cv2
import matplotlib.pyplot as plt
import skimage.io
import numpy as np
from skimage.feature import graycomatrix, graycoprops
```
Codingan ini mengimpor pustaka OpenCV, Matplotlib, scikit-image, dan NumPy untuk pemrosesan gambar dan perhitungan fitur tekstur. OpenCV digunakan untuk mengonversi gambar ke grayscale, Matplotlib untuk menampilkan gambar, dan scikit-image untuk membaca gambar dari file. NumPy digunakan untuk operasi numerik, sedangkan fungsi graycomatrix dan graycoprops dari scikit-image menghitung matriks ko-okurensi tingkat abu-abu (GLCM) dan propertinya, seperti kontras dan homogenitas, yang membantu menganalisis tekstur gambar.

-Membaca Gambar
```
img = skimage.io.imread('2.jpg')
```
