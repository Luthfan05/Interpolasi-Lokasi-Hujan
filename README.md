# Interpolasi Bilinear Curah Hujan ke Titik Lokasi

Notebook ini berisi skrip Python untuk melakukan **interpolasi bilinear** data curah hujan (CH) ke titik-titik koordinat spesifik berdasarkan berbagai sumber data spasial, seperti **CHIRPS**, **ERA5**, **IMERG**, dan **GSMaP**. Notebook ini dirancang untuk memproses data raster/grid dan mengambil nilai curah hujan pada titik-titik observasi (misalnya stasiun) secara efisien.

## Daftar Isi
- [Deskripsi Umum](#deskripsi-umum)
- [Sumber Data](#sumber-data)
- [Fungsi Utama](#fungsi-utama)
---

## Deskripsi Umum

Interpolasi bilinear dilakukan terhadap dataset raster spasial agar nilai di titik tertentu (misalnya dari file CSV berisi koordinat lokasi) dapat diestimasi. Bila interpolasi bilinear menghasilkan nilai `NaN`, metode fallback ke **nearest-neighbor interpolation** digunakan.

## Sumber Data

Notebook ini mendukung pemrosesan data dari berbagai sumber:
- **CHIRPS** (`.tif` atau `.bil`)
- **ERA5** (`.nc`)
- **IMERG** (`.nc4`)
- **GSMaP** (`.nc` atau `.h5`)

Format file input dapat disesuaikan, asalkan memuat informasi spasial (latitude, longitude) dan curah hujan dalam grid.

## Fungsi Utama

Beberapa fungsi penting yang terdapat dalam notebook:
- `load_coordinates(csv_file)`: Memuat titik koordinat dari file CSV.
- `interpolate_bilinear(raster_file, points_df)`: Mengambil nilai CH berdasarkan interpolasi bilinear.
- `interpolate_with_fallback(raster_file, points_df)`: Menggunakan interpolasi bilinear, dan fallback ke nearest-neighbor jika `NaN`.
- `process_all_files(folder_path)`: Memproses semua file raster dari satu folder dan menyimpan hasilnya dalam bentuk `.csv`.
