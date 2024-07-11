UAS PENGOLAHAN CITRA DIGITAL B
Nama : Aldha Nitha Try Wulan Sari
Nim : 202231057

Teori :
Transformasi Geometri pada Citra:
Transformasi geometri adalah teknik dalam pemrosesan citra yang digunakan untuk mengubah bentuk, ukuran orientasi, atau tatak letak suatu citra. Dalam konteks pemrosesan citra, transformasi geometri adalah salah satu metode yang paling umum digunakan untuk mengubah citra menjadi bentuk yang lebih mudah dianalisis atau memperbaiki tampilannya. 

Flip Horizontal : adalah transformasi yang menghasilkan citra asli secara horizontal. Piksel yang awalnya berada disisi kiri citra akan berada disisi kanan citra hasil, dan sebaliknya. ini mirip dengan melihat citra di cermin horizontal.

Rotasi searah jarum jam: Citra diputar searah jarum jam. Ini berarti bahwa piksel yang kembali berada dibagian atas citra akan dipindahkan ke sisi kanan citra.

Translasi: Operasi translasi adalah memindahkan setiap elemen piksel citra input ke posisi baru pada citra ouput dimana dimensi dari kedua citra (citra masukan dan citra ouput) pada umumnya adalah sama. Posisi baru dari suatu piksel ditentukan dari nilai variabel translasi(p,q).

Penskalaan: adalah sebuah proses operasi geometri yang memberikan efek memperbesar atau memperkecil ukuran citra input sesuai dengan variabel Penskalaan citranya.

Penjelasan Codingan : 

1. import cv2 -> cv2 dari OpenCV untuk pemrosesan gambar.
2. import numpy as np -> numpy sebagai np untuk operasi pada array.
3. import matplotlib.pyplot as plt -> matplotlib.pyplot sebagai plt untuk visualisasi gambar.
4. image = cv2.imread('Aldha.jpg') -> Membaca gambar dengan nama file Aldha.jpg menggunakan OpenCV.
5. def show_images(images, titles):
    fig, axes = plt.subplots(1, len(images), figsize=(20, 10))
    for idx, ax in enumerate(axes):
        ax.imshow(cv2.cvtColor(images[idx], cv2.COLOR_BGR2RGB))
        ax.set_title(titles[idx])
        ax.axis('off')
    plt.show() -> Fungsi show_images ini digunakan untuk menampilkan beberapa gambar dalam satu baris dengan menggunakan Matplotlib. Fungsi ini menerima dua argumen: images (list gambar) dan titles (list judul untuk setiap gambar).
6. original_image = image.copy() -> Menyalin gambar asli untuk disimpan sebagai referensi.
7. (height, width) = image.shape[:2]
center = (width // 2, height // 2)
rotation_matrix = cv2.getRotationMatrix2D(center, 45, 1.0)
rotated_image = cv2.warpAffine(image, rotation_matrix, (width, height)) -> Merotasi gambar sebesar 45 derajat searah jarum jam di sekitar titik tengah gambar.
8. resized_image = cv2.resize(image, (width // 2, height // 2)) -> Mengubah ukuran gambar menjadi setengah dari ukuran aslinya.
9. start_x, start_y = width // 4, height // 4
end_x, end_y = start_x + width // 4, start_y + height // 4
cropped_image = image[start_y:end_y, start_x:end_x] -> Memotong bagian dari gambar mulai dari titik (start_x, start_y) hingga titik (end_x, end_y).
10. flipped_image = cv2.flip(image, 1) -> Membalik gambar secara horizontal.
11. translation_matrix = np.float32([[1, 0, 100], [0, 1, 50]])
translated_image = cv2.warpAffine(image, translation_matrix, (width, height)) -> Menggeser gambar sebesar 100 piksel ke kanan dan 50 piksel ke bawah.
12. images_list = [original_image, rotated_image, resized_image, cropped_image, flipped_image, translated_image]
titles_list = ['Gambar Asli', 'Setelah Rotasi', 'Setelah Resize', 'Setelah Crop', 'Setelah Flip', 'Setelah Translasi']

show_images(images_list, titles_list) -> Membuat list dari semua gambar yang telah ditransformasi beserta judulnya, lalu menampilkan semuanya dalam satu baris menggunakan fungsi show_images.


