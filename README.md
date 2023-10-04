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


TUGAS 4

1.	Apa itu Django UserCreationForm, dan jelaskan apa kelebihan dan kekurangannya?

Djago UserCreationForm adalah formulir bawaan yang disediakan oleh Django untuk memudahkan proses penciptaan user baru dalam aplikasi web yang menggunakan Django. Class ini termasuk dalam modul django.contrib.auth.forms dan berfungsi untuk mengumpulkan data yang diperlukan untuk membuat akun.

Kelebihan:
- Mudah Digunakan: UserCreationForm mempermudah proses pembuatan alur register yang cepat dan mudah, sehingga mempercepat pembuatan aplikasi.
- Terintegrasi dengan Keamanan Django: Password yang disimpan melalui formulir akan di hash oleh Django, sehingga meningkatkan keamanan penyimpanan password.
- Validasi Password yang Kuat: Formulir ini memberlakukan syarat-syarat tertentu pada password, seperti panjang minimum dan keharusan mengandung karakter khusus, sehingga membuat password menjadi lebih kuat.

Kekurangan:
- Terbatas: Formulir standar UserCreationForm hanya menerima input username, alamat email, dan password. Jika memerlukan input tambahan, formulir ini harus di custom terlebih dahulu.
- Tidak Mendukung Verifikasi Email: Formulir ini hanya digunakan untuk membuat akun user dalam aplikasi. Jika diperlukan langkah-langkah tambahan seperti verifikasi email, maka perlu di custom.


2. Apa perbedaan antara autentikasi dan otorisasi dalam konteks Django, dan mengapa keduanya penting?

-	Autentikasi: Proses memverifikasi identitas pengguna, yang dalam Django melibatkan pengenalan pengguna (login) seperti memeriksa nama pengguna dan password.

-	Otorisasi: Proses memverifikasi hak akses pengguna terhadap sistem atau program.

Keduanya memiliki peran krusial dalam menjaga keamanan. Autentikasi berfokus pada memastikan identitas pengguna yang benar, mencegah akses yang tidak sah, serta menjaga kerahasiaan data sensitif. Di sisi lain, otorisasi bertujuan untuk memastikan bahwa pengguna hanya memiliki akses ke bagian sistem yang sesuai dengan peran atau izin yang dimilikinya.


3.	Apa itu cookies dalam konteks aplikasi web, dan bagaimana Django menggunakan cookies untuk mengelola data sesi pengguna?

Cookies merupakan file kecil yang disimpan pada komputer pengguna oleh situs web yang mereka kunjungi. Fungsinya adalah untuk menyimpan informasi mengenai pengguna dan preferensi mereka, seperti login, pilihan bahasa, dan jejak pencarian. Dalam konteks aplikasi web, cookies digunakan untuk mengatur data sesi pengguna, yang mencakup informasi yang disimpan oleh server tentang pengguna selama mereka menggunakan aplikasi web. 

Dalam Django, cookies digunakan untuk mengelola data sesi pengguna dengan cara menyimpan session ID pada cookie. Ketika pengguna mengakses aplikasi web, Django akan menciptakan session ID yang baru dan menyimpannya dalam cookie. Tiap kali pengguna mengirim permintaan ke server, session ID ini akan dikirimkan bersama permintaan tersebut. Server kemudian akan menggunakan session ID ini untuk mengambil data sesi pengguna dari penyimpanan server dan mengirimkannya kembali ke pengguna. Melalui penggunaan cookies ini, Django dapat mengelola data sesi pengguna dengan cara yang aman dan efisien.


4.	Apakah penggunaan cookies aman secara default dalam pengembangan web, atau apakah ada risiko potensial yang harus diwaspadai?

Penggunaan cookies dalam pengembangan web dapat menjadi alat yang aman jika diterapkan dengan cermat, tetapi juga bisa memiliki risiko potensial jika tidak diawasi secara ketat. 

Risiko potensial yang perlu diperhatikan:
- Cross-Site Scripting (XSS): Serangan XSS digunakan untuk cookies, menyebar malware session hijacking/pembajakan session, dan mengarahkan tujuan/malicious redirects
- Cross-Site Request Forgery (CSRF): CSRF merupakan serangan eksploitasi web yang menjadikan pengguna secara tidak sadar mengirimkan permintaan ke situs web tertentu melalui situs web yang sedang mereka gunakan saat itu.
- Cookie Theft: Pencurian cookie ini merupakan risiko lainnya. Jika penyerang dapat mengakses cookie pengguna, mereka bisa mencuri data sensitif atau mengendalikan sesi pengguna.
- Insecure Transmission: Cookies dikirimkan antara perangkat pengguna dan server dalam teks terbuka, kecuali jika dienkripsi. Jika cookies mengandung informasi sensitif seperti password, maka ada risiko intercept cookies melalui serangan Man-in-the-Middle (MITM).
- Cookie Sniffing: Penyerang yang memiliki akses fisik atau ke jaringan dapat mencoba mencuri cookies dengan metode seperti packet sniffing.

Untuk mengatasi risiko-risiko yang sudah disebutkan, perlu diambil tindakan keamanan khusus selama proses pengembangan web.


5.	Jelaskan bagaimana cara kamu mengimplementasikan checklist di atas secara step-by-step (bukan hanya sekadar mengikuti tutorial).

A.	Mengimplementasikan fungsi registrasi, login, dan logout untuk memungkinkan pengguna untuk mengakses aplikasi sebelumnya dengan lancar.

o   Membuat fungsi registrasi
    - Dalam views.py direktori aplikasi main, import beberapa library berikut

    from django.shortcuts import redirect
    from django.contrib.auth.forms import UserCreationForm
    from django.contrib import messages  

    Buat fungsi baru dengan nama register yang meminta parameter request dan diisi dengan kode berikut

    def register(request):
    form = UserCreationForm()

    if request.method == "POST":
        form = UserCreationForm(request.POST)
        if form.is_valid():
            form.save()
            messages.success(request, 'Your account has been successfully created!')
            return redirect('main:login')
    context = {'form':form}
    return render(request, 'register.html', context)

    Kemudian, di dalam direktori template pada direktori aplikasi main, buat file dengan nama register.html untuk membuat halaman yang akan ditampilkan saat register. Buat routing pada urls,py direktori aplikasi main

o	Membuat fungsi login
    - Dalam views.py direktori aplikasi main, import beberapa library berikut

    from django.contrib.auth import authenticate, login

    Selanjutnya, buat fungsi baru bernama login_user di views.py direktori aplikasi dan diisi dengan kode berikut

    def login_user(request):
    if request.method == 'POST':
        username = request.POST.get('username')
        password = request.POST.get('password')
        user = authenticate(request, username=username, password=password)
        if user is not None:
            login(request, user)
            response = HttpResponseRedirect(reverse("main:show_main")) 
            response.set_cookie('last_login', str(datetime.datetime.now()))
            return response
        else:
            messages.info(request, 'Sorry, incorrect username or password. Please try again.')
    context = {}
    return render(request, 'login.html', context)

    Manfaatkan cookie dengan menambahkan line response.set_cookie('last_login', str(datetime.datetime.now())) saat user berhasil login dengan key last_login dan value tanggal login saat itu. Pada direktori template buat file login.html untuk membuat halaman yang akan ditampilkan saat register. Buat routing pada urls.py direktori aplikasi.

o	Membuat fungsi logout
    - Dalam views.py direktori aplikasi main, import beberapa library berikut

    from django.contrib.auth import logout

    Lalu, buatfungsi baru logout_user di views.py direktori aplikasi kemudian diisi dengan kode berikut

    def logout_user(request):
    logout(request)
    response = HttpResponseRedirect(reverse('main:login'))
    response.delete_cookie('last_login')
    return response

    Dilakukan penghapusan cookie dengan key last_login saat user logout. Lalu, buat routing pada urls.py direktori aplikasi

o	Restriksi akses aplikasi
    - Dalam views.py import login_required dan tambahkan @login_required(login_url='/login') di atas fungsi show_main

B.	Membuat dua akun pengguna dengan masing-masing tiga dummy data menggunakan model yang telah dibuat pada aplikasi sebelumnya untuk setiap akun di lokal.

o	Register untuk 2 akun dan tambahkan 3 produk pada setiap akun.

<img src="/Gambar//Akun1.jpg">

<img src="/Gambar//Akun2.jpg">

C.	Menghubungkan model Item dengan User.

o	Dalam models.py import user kemudian tambahkan user = models.ForeignKey(User, on_delete=models.CASCADE) ke dalam class model Item. Ubahlah fungsi create_product dengan kode di bawah agar buku yang dibuat terasosiasi pada satu user

def create_product(request):
  form = ProductForm(request.POST or None)

  if form.is_valid() and request.method == "POST":
      product = form.save(commit=False)
      product.user = request.user
      product.save()
      return HttpResponseRedirect(reverse('main:show_main'))
...

D.	Menampilkan detail informasi pengguna yang sedang logged in seperti username dan menerapkan cookies seperti last login pada halaman utama aplikasi.

o	Menampilkan username pengguna
Pada fungsi show_main di views.py ubah isi context dengan key 'name' menjadi

'name': request.user.username,

o	Menerapkan cookies last login
Penerapan cookies sudah dijelaskan dan untuk menampilkan last login, tambahkan kode berikut pada context fungsi show_main

'last_login': request.COOKIES['last_login'],

Lalu pada main.html tambahkan kode berikut

<h5>Last login session: {{ last_login }}</h5>



TUGAS 5

1. Jelaskan manfaat dari setiap element selector dan kapan waktu yang tepat untuk menggunakannya.

    A.Elemen Selector: Memilih elemen dengan nama elemen tertentu. Ini berguna ketika ingin mengubah gaya semua elemen teks paragraf pada halaman web secara seragam.

        p {
            text-align: center;
            color: red;
        }

    B. ID Selector: Memilih elemen dengan ID tertentu yang harus unik dalam satu halaman. Cocok digunakan untuk mengidentifikasi elemen tertentu.

        #para1 {
            text-align: center;
            color: red;
        }

    C. Class Selector: Mengganti gaya elemen dengan class tertentu. Ini berguna saat ingin menerapkan gaya yang sama pada beberapa elemen, tetapi tidak semua elemen dengan tag yang sama.

        .center {
            text-align: center;
            color: red;
        }

    D. Universal Selector: Universal selector akan mempengaruhi semua elemen pada halaman. Ini digunakan ketika ingin mengubah gaya menjadi seragam pada semua elemen halaman.

        * {
            text-align: center;
            color: blue;
        }

    E. Grouping Selector: Mengganti gaya elemen yang berbeda-beda. Kita bisa mendefinisikan gaya elemen yang berbeda-beda tersebut ke dalam satu grup.

        h1, h2, p {
            text-align: center;
            color: red;
        }


2.	Jelaskan HTML5 Tag yang kamu ketahui.

    - <table> : Membuat tabel
    - <td> : Membuat masing-masing item dari tabel
    - <tr> : Membuat baris tabel
    - <h1> - <h6> : Membuat heading, h1 paling besar dan penting, h6 paling kecil dan tingkatannya paling kecil
    - <p> : Membuat paragraf
    - <div> : Menentukan bagian dalam halaman
    - <body> : Menentukan badan suatu elemen
    - <title> : Menentukan judul
    - <button> : Membuat tombol


3.	Jelaskan perbedaan antara margin dan padding.

    A. Margin
        - Ruang di sekitar suatu elemen dalam HTML
        - Penggunaan margin memungkinkan kita mengontrol jarak antara suatu elemen dengan elemen-elemen lain dalam halaman HTML
        - Kita dapat mengatur margin dari berbagai sisi, seperti margin-top, margin-left, margin-right, dan margin-bottom
        - Contoh:

            section {
                margin-top: 5px;
                margin-right: 20px;
                margin-bottom: 5px;
                margin-left: 20px;
            }

    B. Padding
        - Ruang di dalam elemen HTML, di antara kontennya dan batas elemen itu sendiri. 
        - Padding berguna untuk mengendalikan jarak antara konten elemen dengan batas elemen tersebut
        - Padding juga dapat diatur dari berbagai sisi, seperti padding-top, padding-left, padding-right, dan padding-bottom
        - Contoh:

            section {
                padding-top: 15px;
                padding-right: 30px;
                padding-bottom: 15px;
                padding-left: 30px;
            }

    Perbedaan antara margin dan padding terletak pada pengaturan jarak. Margin mengatur jarak di sekitar elemen, sedangkan padding mengatur ruang di dalam elemen antara kontennya dan batas elemen itu sendiri.


4. Jelaskan perbedaan antara framework CSS Tailwind dan Bootstrap. Kapan sebaiknya kita menggunakan Bootstrap daripada Tailwind, dan sebaliknya?

    A. Filosofi Desain
        - Bootstrap: Lebih terstruktur dan konsisten. Memiliki gaya desain yang lebih formal dan dapat lebih mudah diimplementasikan oleh pengembang yang mungkin tidak memiliki latar belakang desain yang kuat.
        - Tailwind: Lebih fleksibel dan memberikan lebih banyak kebebasan dalam desain. Memungkinkan pengembang untuk menciptakan desain yang lebih unik dan kreatif sesuai dengan preferensi mereka.

    B. Ukuran File
        - Bootstrap: Memiliki ukuran file yang lebih besar daripada Tailwind karena Bootstrap menyediakan banyak fitur.
        - Tailwind: Memiliki ukuran file yang lebih kecil daripada Bootstrap karena pendekatan yang lebih modular dan fleksibel dalam penggunaan kelas-kelas CSS.

    C. Kustomisasi
        - Bootstrap: Menyediakan banyak tema dan template yang dapat mempercepat pengembangan. Namun, kustomisasi yang lebih lanjut bisa menjadi sulit karena memiliki banyak aturan dan struktur yang harus diikuti.
        - Tailwind: Memungkinkan pengembang lebih kreatif dalam membuat desain. Dengan Tailwind, pengembang dapat menjadi lebih bebas karena mereka dapat membuat kelas-kelas CSS sesuai kebutuhan.

    D. Penggunaan
        - Bootstrap: Lebih sesuai untuk proyek-proyek yang membutuhkan desain yang konsisten dan dapat diimplementasikan dengan mudah. Maka cocok untuk proyek-dengan tenggat waktu pengembangan yang cepat.
        - Tailwind: Lebihsesuai untuk proyek-proyek yang menekankan desain yang unik dan kreatif. Maka cocok untuk proyek-proyek yang membutuhkan tingkat kustomisasi yang lebih dalam dan fleksibilitas dalam penggunaan kelas-kelas CSS.

    Sebaiknya menggunakan Bootstrap jika membutuhkan desain yang konsisten dan mudah diimplementasikan, serta membutuhkan waktu pengembangan yang cepat. Sedangkan Tailwind, sebaiknya digunakan jika membutuhkan desain yang lebih unik dan kreatif, serta membutuhkan tingkat kustomisasi yang lebih dalam dan fleksibilitas dalam penggunaan kelas-kelas CSS.


5. Jelaskan bagaimana cara kamu mengimplementasikan checklist di atas secara step-by-step (bukan hanya sekadar mengikuti tutorial).

    Untuk melakukan kustomisasi, saya menggunakan file external CSS dengan Langkah-langkah berikut:
        - Membuat direktori baru bernama “static” dalam direktori aplikasi main
        - Membuat folder CSS di dalam direktori “static” yang berisi file-file CSS dari file html yang saya buat sebelumnya
        - Agar file HTML terhubung dengan file CSS, saya menambahkan kode berikut di setiap berkas HTML:
        
            {% load static %}

            {% block meta %}
                <meta charset="UTF-8">
                <meta name="viewport" content="width=device-width, initial-scale=1.0">
                <link rel="stylesheet" href="{% static 'css/filename.css' %}">
                <title>Title</title>
            {% endblock meta %}

    Kemudian, saya melakukan kustomisasi pada page login, register, main, edit_product, dan create_product. Dalam mengubah desain page, saya membagi setiap bagian HTML ke dalam class yang berbeda untuk memungkinkan kustomisasi yang lebih detail. Beberapa command yang sering digunakan adalah padding, margin, width, dan height. Saya juga mengubah background dari HTML dengan menggunakan background-image dan memasukkan link gif dalam file CSS.

    Selanjutnya, saya menambahkan fitur card ke dalam halaman main. Untuk melakukannya, saya menambahkan dan melakukan sedikit memodifikasi potongan kode dari Bootstrap seperti di bawah ini:

        <div class="card-container">
            {% for product in products %}
            <div class="card" style="width: 18rem;">
                <div class="card-body">
                    <h5 class="card-title">{{product.name}}</h5>
                    <p class="card-text">{{product.price}}</p>
                </div>
            </div>
            {% endfor %}
        </div>

    Dalam potongan kode Bootstrap tersebut, elemen card dihubungkan dengan objek products. Sebagai contoh, pada bagian card-title elemennya adalah {{product.name}}, dan pada bagian card-text elemennya adalah {{product.price}}. Setelah menambahkan potongan kode untuk card, saya melakukan kustomisasi lebih lanjut pada card dalam file main.css seperti berikut:

        .card-container {
            display: grid;
            grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
            grid-gap: 20px;
            margin: 40px;
            justify-content: center;
            justify-items: center;
            padding-bottom: 20px;
        }

        .card-container .card {
            max-width: 100%;
            border: 2px solid #ff1493;
            box-shadow: 2px 3px 8px 10px #ff1493;
        }

        .card-container .card-title {
            font-weight: bold;
            color: #ff007f;
        }

        .card-container .card-text {
            color: #555;
        }