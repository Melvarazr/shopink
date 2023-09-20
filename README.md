TUGAS 2

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


TUGAS 3

1. Apa perbedaan antara form POST dan form GET dalam Django?

POST: 
- Lebih aman
- Data tidak ditampilkan di URL, disimpan di dalam badan permintaan HTTP
- Tidak ada batasan panjang URL yang perlu dikhawatirkan
- Umumnya digunakan untuk input data melalui form

Metode GET (HTTP GET):
- Kurang aman
- Data ditambahkan ke URL, sehingga dapat dilihat oleh siapa saja.
- Ada batasan panjang URL yang perlu diperhatikan
- Umumnya digunakan untuk input data melalui link

2. Apa perbedaan utama antara XML, JSON, dan HTML dalam konteks pengiriman data?

- XML (eXtensible Markup Language): Memiliki struktur yang terspesifikasi, dapat diurai dan diproses, mudah dibaca oleh manusia, mendukung lintas bahasa pemrograman, bertujuan untuk pertukaran data antar aplikasi yang terstuktur
- JSON (JavaScript Object Notation): Memiliki struktur yang ringkas, dapat diurai dan diproses, mudah dibaca oleh manusia, mendukung lintas bahasa pemrograman, bertujuan untuk pertukaran data antar aplikasi yang lebih ringkas dan mudah dimengerti
- HTML (Hypertext Markup Language): Memiliki struktur yang spesifik, tidak dapat diurai, mudah dibaca oleh manusia, tidak mendukung lintas bahasa pemrograman, bertujuan untuk menciptakan tampilan halaman web dan bukan untuk pemrosesan data

3. Mengapa JSON sering digunakan dalam pertukaran data antara aplikasi web modern?

JSON umumnya digunakan dalam pertukaran data antara aplikasi web modern karena formatnya yang simpel dan mudah dimengerti, sehingga developer tidak menghadapi kesulitan dalam memahami struktur data JSON dibandingkan dengan struktur data lainnya. Selain itu, JSON juga lebih efisien dalam ukuran penyimpanan data.

4. Jelaskan bagaimana cara kamu mengimplementasikan checklist di atas secara step-by-step (bukan hanya sekadar mengikuti tutorial).

A. Membuat input form untuk menambahkan objek model pada app sebelumnya.

- Dalam direktori aplikasi main, buatlah sebuah berkas forms.py
- Di dalam berkas forms.py tersebut, buatlah sebuah class ProductForm yang memiliki argumen ModelForm
- Pada class ProductForm, buatlah sebuah class Meta yang berisi model yang digunakan, dalam konteks ini model=Item. Selain itu, berisi juga fields yang bisa disi user yaitu fields = ["name", "price", "description", "genre" "amount" ]
- Membuat fungsi create_product di dalam views.py yang menerima parameter request. Di dalam create_ product, kita membuat sebuah ProductForm baru yang disi dengan argumen request.POST dalam bentuk QueryDict . Kemudian kita memvalidasi kontennya dengan menggunakan form.is_valid() dan menyimpan kontennya dengan menggunakan form.save() . Jika kontennya berhasil disimpan, kembali ke halaman utama dengan menggunakan return HttpResponseRedirect(rev erse ('main:show main')) . Fungsi tersebut akan menampilkan create_product.html.
- Di dalam views.py, buatlah sebuah fungsi bernama create_product yang menerima parameter request. Dalam fungsi ini, buatlah ProductForm baru yang diisi dengan argumen request.POST dalam bentuk QueryDict. Kemudian, lakukan validasi data menggunakan form.is_valid() dan simpan menggunakan form.save(). Jika penyimpanan berhasil, kembali ke halaman utama dengan return HttpResponseRedirect(rev erse ('main:show main')). Fungsi ini akan menampilkan create_product.html
- Memodifikasi show_main dalam views.py dengan menambahkan item = Item.objects.all() untuk menampilkan data item yang telah ditambahkan, dan juga menambahkan item_count = item.count() untuk menghitung jumlah total item yang tersedia.
- Melakukan routing di urls.py di direktori aplikasi main dengan menambahkan path ('create-product' create_product, name='create_product') di urlpatterns
- Buat tampilan create_product dengan menambahkan create_product.html ke dalam templates pada main. Isi berkas HTML tersebut dengan kode yang tepat untuk menampilkan formulir dalam format tabel, pastikan menggunakan {% csrf token %} untuk security, dan gunakan tag <form method="POST"> untuk menandai formulir dengan metode POST.

B. Tambahkan 5 fungsi views untuk melihat objek yang sudah ditambahkan dalam format HTML, XML, JSON, XML by ID, dan JSON by ID.

- HTML
    - Penjelasan telah diberikan sebelumnya dalam poin pertama dan ditampilkan di main.html yang menggunakan fungsi show_main dari views.py
- XML
    - Buat fungsi show_xml di dalam views.py dan kemudian isilah dengan kode berikut agar data yang diambil dari objek model Item dapat direturn dalam format XML

    def show_xml(request):
    data = Item.objects.all()
    return HttpResponse(serializers.serialize("xml", data), content_type="application/xml")

    Serializers bertujuan untuk mentranslasikan objek model ke xml
- JSON
    - Buat fungsi show_json di dalam views.py dan selanjutnya isilah dengan kode berikut agar data yang diambil dari objek model Item dapat direturn dalam format JSON

    def show_json(request):
    data = Item.objects.all()
    return HttpResponse(serializers.serialize("json", data), content_type="application/json")

    Serializers bertujuan untuk mentranslasikan objek model ke json
- XML by ID
    - Mengambil objek Item berdasarkan id dan return dalam format XML, tambahkanlah fungsi show_xml_id di dalam views.py dan selanjutnya sertakan kode berikut

    def show_xml_by_id(request, id):
    data = Item.objects.filter(pk=id)
    return HttpResponse(serializers.serialize("xml", data), content_type="application/xml")
- JSON by ID
    - Mengambil objek Item berdasarkan id dan return dalam format JSON, buatlah fungsi show_json_id di dalam views.py dan tambahkan kode berikut

    def show_json_by_id(request, id):
    data = Item.objects.filter(pk=id)
    return HttpResponse(serializers.serialize("json", data), content_type="application/json")

C. Membuat routing URL untuk masing-masing views yang telah ditambahkan pada poin 2.

- HTML
    - Routing telah dilakukan di urls.py dalam aplikasi main, khususnya di bagian

    ...
    path('', show_main, name='show_main'),
    ...
- XML
    - Tambahkanlah routing pada urls.py dalam aplikasi main dengan menggunakan kode path('xml/', show_xml, name='show_xml'), tepatnya di urlpatterns
- JSON
    - Tambahkan routing pada urls.py pada aplikasi main dengan menggunakan kode path('json/', show_json, name='show_json'), tepatnya di urlpatterns
- XML by ID
    - Tambahkan routing pada urls.py pada aplikasi main dengan menggunakan kode path('xml/<int:id>/', show_xml_by_id, name='show_xml_by_id'), tepatnya di urlpatterns
- JSON by ID
    - Tambahkan routing pada urls.py pada aplikasi main dengan menggunakan kode path('json/<int:id>/', show_json_by_id, name='show_json_by_id'), tepatnya di urlpatterns

5. Mengakses kelima URL di poin 2 menggunakan Postman, membuat screenshot dari hasil akses URL pada Postman, dan menambahkannya ke dalam README.md.

HTML
<img src="/Gambar//HTML.jpg">

JSON
<img src="/Gambar//JSON.jpg">

XML
<img src="/Gambar//XML.jpg">

JSON by ID
<img src="/Gambar//JSON1.jpg">

XML by ID
<img src="/Gambar//XML1.jpg">