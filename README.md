# tugas_pemweb_opsional_123140107


---

## Identitas Mahasiswa

**Nama:** Varasina Farmadani
**NIM:** 123140107
**Mata Kuliah:** Pengembangan Aplikasi Web RB
**Tugas:** Tugas Tambahan Nilai UTS (Optional)

---

# 01 — Single-File Web Applications



**Analisis:**
Aplikasi Pyramid dapat dijalankan hanya dari satu file Python menggunakan WSGI + Waitress.
Configurator digunakan untuk mendaftarkan route dan view dalam konteks manager.
View menerima request lalu mengembalikan Response.
Aplikasi dijalankan langsung melalui `python app.py`.
Model ini menunjukkan dasar alur Pyramid: request → routing → view → response.

---

# 02 — Python Packages for Pyramid Applications



**Analisis:**
Aplikasi dipindahkan ke struktur package Python menggunakan direktori `tutorial/` dan `__init__.py`.
`setup.py` mulai digunakan untuk dependency dan instalasi editable (`pip install -e .`).
Cara ini membuat proyek mengikuti standar Python dan bisa dikelola sebagai modul terpisah.
Kode aplikasi tetap sama, hanya cara pengemasannya yang berubah.

---

# 03 — Application Configuration with .ini Files



**Analisis:**
Konfigurasi `.ini` digunakan untuk mendefinisikan entry point WSGI (`main = tutorial:main`).
Startup code dipindahkan ke `tutorial/__init__.py` dengan fungsi `main()`.
Aplikasi dijalankan menggunakan `pserve development.ini --reload`.
`.ini` mengatur server, port, logging, dan memungkinkan pemisahan konfigurasi dari kode.

---

# 04 — Easier Development with debugtoolbar



**Analisis:**
`pyramid_debugtoolbar` ditambahkan sebagai extras `[dev]` di setup.py.
Aktivasi dilakukan melalui `.ini` dengan `pyramid.includes = pyramid_debugtoolbar`.
Toolbar menampilkan informasi debugging, request, traceback, dan environment langsung di browser.
Add-on Pyramid bekerja melalui mekanisme konfigurasi (`config.include()` atau `.ini`).

---

# 05 — Unit Tests and pytest



**Analisis:**
Unit test ditulis dengan `pytest` dan `pyramid.testing`.
`DummyRequest()` digunakan untuk membuat request palsu ke view.
Test memeriksa status code, isi response, atau error.
Import view dilakukan di dalam function test untuk menghindari side effect.
Testing memberikan validasi cepat tanpa membuka browser.

---


# 06 — Functional Testing with WebTest



**Analisis:**
Functional test dilakukan dengan `webtest.TestApp`, yang mensimulasikan HTTP request lengkap tanpa server sungguhan.
Test memeriksa HTML yang dihasilkan aplikasi end-to-end, bukan hanya fungsi view.
`TestApp(app)` menerima aplikasi WSGI dari `main({})` lalu memungkinkan `get('/')` untuk memeriksa response.
Pemeriksaan HTML memakai byte-string (`b'<h1>'`) karena body response berbentuk bytes.

---

# 07 — Basic Web Handling With Views



**Analisis:**
View dipisah ke modul `views.py`, dan konfigurasi view dilakukan dengan dekorator `@view_config`.
`config.scan('.views')` mencari dan mendaftarkan view secara deklaratif.
Dua view (`home` dan `hello`) saling memberi tautan, menunjukkan pemetaan route → view menggunakan deklarasi.
Testing memeriksa status code dan potongan HTML pada body response.
Pendekatan declarative configuration menggantikan konfigurasi imperatif (`config.add_view`).

---

# 08 — HTML Generation With Templating



**Analisis:**
Templating dipindahkan dari Python string ke file template menggunakan `pyramid_chameleon`.
Renderer ditentukan lewat `renderer='home.pt'` pada `@view_config`.
View hanya mengembalikan dictionary data, sedangkan HTML dihasilkan oleh template.
`pyramid.reload_templates = true` memungkinkan auto-reload template saat development.
Testing fokus pada data return view, sementara functional test memeriksa HTML final.

---

# 09 — Organizing Views With View Classes



**Analisis:**
Beberapa view digabung menjadi satu kelas menggunakan `@view_defaults` dan metode view.
State request dibagi melalui `self.request`.
Dekorator class-level mengurangi duplikasi konfigurasi, seperti renderer bersama.
Unit test perlu membuat instance view class lalu memanggil metodenya.
Functional test tetap memakai WebTest untuk memastikan output HTML sesuai.

---

# 10 — Handling Web Requests and Responses



**Analisis:**
Pyramid memakai WebOb sebagai dasar objek request dan response.
Route `/` mengembalikan redirect (`HTTPFound`) ke `/plain`.
View kedua membaca parameter query (`request.params.get('name')`) dan membangun response text/plain.
Testing memeriksa redirect (302) serta isi response untuk kasus dengan dan tanpa parameter.
Functional test menguji perilaku HTTP sebenarnya, termasuk `?name=`.

---


# 11 — Dispatching URLs To Views With Routing



**Analisis:**
Pyramid memungkinkan URL mengandung *replacement pattern* menggunakan `{}` pada deklarasi route, misalnya:

```
/howdy/{first}/{last}
```

`matchdict` pada `request` otomatis berisi nilai hasil ekstraksi pattern tersebut.
View class dapat mengaksesnya melalui:

```python
first = self.request.matchdict['first']
last = self.request.matchdict['last']
```

Nilai ini kemudian diteruskan ke template untuk dirender.
Testing unit dilakukan dengan menetapkan manual:

```python
request.matchdict['first'] = 'First'
request.matchdict['last'] = 'Last'
```

Functional test memakai WebTest memverifikasi bahwa URL seperti `/howdy/Jane/Doe` menampilkan data yang sesuai.

Routing Pyramid mengharuskan route didefinisikan terpisah dari view agar urutan evaluasi route tetap eksplisit dan terkontrol.
Jika URL tidak cocok pattern (misal `/howdy` tanpa argumen), maka route tidak match dan menghasilkan 404.

---


