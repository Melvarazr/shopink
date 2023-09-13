1. Jelaskan bagaimana cara kamu mengimplementasikan checklist di atas secara step-by-step (bukan hanya sekadar mengikuti tutorial).

A. Memulai proyek Django baru

- Buat direktori lokal baru yang disebut "shopink"
- Untuk membuat proyek Django baru, buat Virtual Environment agar direktori tersebut terisolasi dan dependencies tidak bertabrakan. Caranya adalah dengan membuka terminal di direktori yang baru saja saya buat dan mengetikkan perintah: python -m venv env
- Kemudian, untuk mengaktifkan Virtual Environment, jalankan perintah: env\Scripts\activate.bat
- Setelah Virtual Environment aktif, install semua dependencies yang diperlukan. Sebelum itu, buat file "requirements.txt" yang akan diisi dengan dependencies seperti Django dan Gunicorn. Setelah dibuat, kembali ke terminal dengan Virtual Environment dan jalankan perintah berikut untuk menginstal semua dependencies yang diperlukan: pip install -r requirements.txt
- Selanjutnya, untuk membuat proyek Django baru, jalankan perintah: django-admin startproject shopink .
- Karena proyek masih dalam tahap uji coba, tambahkan tanda "*" pada variabel ALLOWED_HOSTS di file "settings.py" agar semua host dapat mengakses aplikasi web. ALLOWED_HOSTS = ["*"]
- Terakhir, tambahkan file ".gitignore" untuk mengabaikan file yang tidak perlu dilacak oleh Git.

B. Untuk membuat aplikasi "main," kembali ke terminal dengan Virtual Environment yang aktif dan jalankan perintah: python manage.py startapp main. Setelah itu, direktori aplikasi "main" akan terbuat. Kemudian, tambahkan aplikasi ini ke dalam variabel "INSTALLED_APPS" di file "settings.py" yang berada dalam direktori proyek "shopink." Selanjutnya, tambahkan direktori "templates" di dalam direktori "main" dan buat file "main.html" di dalam folder tersebut. File HTML ini akan digunakan untuk mengatur tampilan aplikasi "main" pada web.

C. Mengatur routing proyek

- Buka file "urls.py" yang ada di direktori proyek "shopink."
- Impor fungsi "include" dari "django.urls."
- Tambahkan path menuju tampilan "main" ke dalam variabel "urlpatterns" dengan perintah berikut: path('main/', include('main.urls'))

D. Membuat model bernama "Item" di file "models.py," definisikan atribut-atribut berikut:

name
date_added
price
amount
description
genre

E. Di dalam file "views.py" yang berada di direktori aplikasi "main," tambahkan fungsi "show_main" dengan konteks yang berisi nama aplikasi, nama, dan kelas PBP. Pada file "main.html," dapat mengakses isi dari konteks. Misalnya, jika ingin mengambil nama, tuliskan {{name}} di dalam file "main.html."

F. Untuk membuat routing pada aplikasi "main," buat file baru bernama "urls.py" di dalam direktori aplikasi "main." Di dalam file tersebut, impor "path" dari "django.urls" dan "show_main" dari "main.views." Selanjutnya, buat variabel "app_name" yang diisi dengan 'main' dan buat daftar bernama "urlpatterns" yang berisi path kosong (''), mengarah ke fungsi "show_main," dan dinamai 'show_main'.

G. Mendeploy aplikasi ke "adaptable"

- Buat repositori baru di GitHub dan hubungkan repositori lokal "shopink" dengan repositori GitHub.
- Lakukan perintah "add," "commit," dan "push" untuk mengunggah perubahan ke repositori GitHub.
- Terakhir, lakukan proses deployment aplikasi ke "adaptable."


2. Buatlah bagan yang berisi request client ke web aplikasi berbasis Django beserta responnya dan jelaskan pada bagan tersebut kaitan antara urls.py, views.py, models.py, dan berkas html.
<img src="/Gambar//Gambar no 2.jpg">

- Pertama, client akan meminta browsernya untuk mengakses situs berbasis Django.
- Kemudian, browser akan mengirimkan permintaan (HTTP Request) ke server untuk mengambil halaman web.
- Permintaan tersebut akan diarahkan ke sistem routing yang dikelola oleh Django untuk mencari pola URL yang cocok dengan permintaan client.
- Setelah pola URL yang sesuai telah ditemukan, Django akan menjalankan fungsi yang terkait dalam berkas views.py yang terhubung dengan URL tersebut.
- Di dalam berkas views.py, kita dapat menjalankan alur aplikasi dan operasi basis data sesuai dengan arsitektur sudah ditentukan dalam models.py.
- Setelah semua operasi selesai, fungsi yang dipilih dalam berkas views.py akan menghasilkan halaman web yang diminta oleh client dalam berkas HTML atau template
- Berkas HTML akan disimpan dalam direktori templates untuk selanjutnya
- Terakhir, browser client akan merender berkas HTML ini sebagai respons (HTTP Response) dari server Django, sehingga menghasilkan tampilan yang dilihat oleh pengguna.

3. Jelaskan mengapa kita menggunakan virtual environment? Apakah kita tetap dapat membuat aplikasi web berbasis Django tanpa menggunakan virtual environment?

Pentingnya Virtual Environment dalam pembuatan proyek Django terletak pada kemampuannya untuk memisahkan modul yang digunakan dalam proyek, menghindari konflik, dan menjaga tingkat keamanan. Dengan demikian, virtual environment memungkinkan pengembangan proyek yang lebih efisien dan terstruktur, serta mencegah masalah yang mungkin timbul akibat ketidakcocokan versi modul. Oleh karena itu, dengan menggunakan virtual environment, proyek dapat dikerjakan secara paralel dengan proyek lain, lebih baik daripada menggunakan lingkungan global.

4. Jelaskan apakah itu MVC, MVT, MVVM dan perbedaan dari ketiganya.

MVC: MVC (Model View Controller) adalah bagian yang mengelola data dan logika aplikasi atau situs web, serta menjembatani koneksi dengan database. View bertanggung jawab atas tampilan yang dilihat oleh pengguna. Sementara itu, Controller mengatur hubungan antara Model dan View, memproses permintaan pengguna, dan mengubah View.

MVT: MVT (Model View Template) adalah komponen yang mengurus data dan logika inti aplikasi atau situs web. Dalam MVT, View bertindak seperti controller, mengambil data dari model dan mengatur tampilan data. Template adalah representasi visual dari aplikasi atau situs web yang terlihat oleh pengguna.

MVVM: MVVM (Model View ViewModel) adalah komponen yang mengelola data dan logika inti. View mengatur tampilan yang terlihat oleh pengguna. ViewModel berfungsi untuk data binding, dan pembaruan Model.

Perbedaan: Dalam membahas perbedaannya, MVC dan MVT memiliki kesamaan, tetapi dalam MVT, View berperan seperti controller dalam mengatur pengambilan data, pada MVT juga memiliki komponen Template untuk menampilkan visual. MVVM lebih berfokus pada data binding, dengan ViewModel yang mengambil data dari Model dan mengubahnya ke format yang mudah dibaca oleh View. MVC dan MVT umumnya digunakan untuk aplikasi atau situs web biasa, sedangkan MVVM cocok untuk aplikasi dengan UI kompleks.