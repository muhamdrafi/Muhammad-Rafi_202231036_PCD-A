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
Codingan ini untuk mengimpor gambar dari file dengan nama file 2.jpg

-Konversi Gambar RGB ke HSV
```
img_hsv = cv2.cvtColor(img, cv2.COLOR_RGB2HSV)
```
Codingan ini mengonversi gambar dari RGB ke HSV menggunakan cv2.cvtColor dari OpenCV. Gambar input img dalam format RGB diubah menjadi ruang warna HSV, dan hasilnya disimpan dalam variabel img_hsv, memisahkan informasi warna dari intensitas untuk analisis dan manipulasi yang lebih mudah.

-Melakukan Ekstraksi Kanal V Dari Gambar HSV
```
img_v = img_hsv[:, :, 2]
```
Codingan ini mengekstrak kanal Value (V) dari gambar dalam ruang warna HSV. Dengan img_hsv[:, :, 2],lalu codingan ini mengambil seluruh gambar img_hsv dan memilih kanal ketiga (indeks 2), yang mewakili tingkat kecerahan atau intensitas, dan menyimpannya dalam variabel img_v.

-Melakukan GLCM Pada Kanal V
```
glcm = graycomatrix(img_v, distances=[1], angles=[0], levels=256, symmetric=True, normed=True)
```
Codingan ini menghitung matriks ko-okurensi tingkat abu-abu (GLCM) dari kanal Value (V) gambar HSV yang disimpan dalam img_v. Dengan graycomatrix, GLCM dihitung untuk jarak piksel 1 dan sudut 0 derajat, dengan 256 tingkat abu-abu. Parameter symmetric=True memastikan GLCM simetris, dan normed=True menormalkan matriks, menghasilkan frekuensi relatif. Hasilnya disimpan dalam variabel glcm.

-Melakukan Plot Gambar RGB dan HRV
```
fig, axs = plt.subplots(1, 3, figsize=(20, 10))

ax = axs.ravel()

ax[0].imshow(img)
ax[0].set_title("RGB")

ax[1].imshow(img_hsv)
ax[1].set_title("HSV")

ax[2].imshow(img_v, cmap='gray')
ax[2].set_title("Kanal V dari HSV")

plt.show()
```
Codingan ini menggunakan matplotlib untuk membuat subplot dengan tiga gambar berbeda dalam satu figur. Subplot pertama menampilkan gambar asli dalam ruang warna RGB (img). Subplot kedua menampilkan gambar yang telah dikonversi ke ruang warna HSV (img_hsv). Subplot ketiga menampilkan kanal Value (V) dari gambar dalam ruang warna HSV (img_v), ditampilkan dengan menggunakan colormap 'gray' untuk menunjukkan intensitas piksel. Ukuran figur ditentukan dengan figsize=(20, 10). Setiap subplot diberi judul yang sesuai dengan jenis gambar yang ditampilkan. Hasilnya adalah tiga gambar yang ditampilkan secara berdampingan untuk membandingkan antara ruang warna RGB dan HSV, serta visualisasi kanal V dari ruang warna HSV.

-Menghitung Properti dari GLCM
```
contrast = graycoprops(glcm, 'contrast')[0, 0]
dissimilarity = graycoprops(glcm, 'dissimilarity')[0, 0]
homogeneity = graycoprops(glcm, 'homogeneity')[0, 0]
energy = graycoprops(glcm, 'energy')[0, 0]
correlation = graycoprops(glcm, 'correlation')[0, 0]
ASM = graycoprops(glcm, 'ASM')[0, 0]
```
Kode ini menghitung beberapa properti dari matriks ko-okurensi tingkat abu-abu (GLCM) yang sudah dihitung sebelumnya (glcm). Properti yang dihitung meliputi kontras, dissimilaritas, homogenitas, energi, korelasi, dan ASM (Angular Second Moment). Setiap nilai properti diambil dari hasil yang dikembalikan oleh fungsi graycoprops untuk posisi piksel [0, 0] dalam matriks GLCM. Properti ini memberikan informasi tentang pola dan distribusi nilai piksel dalam gambar, yang penting dalam analisis tekstur gambar.

-Lalu Print/input Properti GLCM
```
print(f"Contrast: {contrast}")
print(f"Dissimilarity: {dissimilarity}")
print(f"Homogeneity: {homogeneity}")
print(f"Energy: {energy}")
print(f"Correlation: {correlation}")
print(f"ASM: {ASM}")
```
Codingan ini mencetak nilai properti-properti yang telah dihitung sebelumnya dari matriks ko-okurensi tingkat abu-abu (GLCM). Properti yang dicetak meliputi kontras, dissimilaritas, homogenitas, energi, korelasi, dan ASM (Angular Second Moment). Setiap nilai properti diprint menggunakan f-string untuk memformat output.
