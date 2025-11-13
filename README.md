# tugas_pemweb_opsional_123140107

Repository: **[https://github.com/sinavarasina/tugas_pemweb_opsional_123140107](https://github.com/sinavarasina/tugas_pemweb_opsional_123140107)**

## Identitas Mahasiswa

**Nama:** Varasina Farmadani  
**NIM:** 123140107  
**Mata Kuliah:** Pengembangan Aplikasi Web  
**Tugas:** Tugas Tambahan Nilai UTS (Optional)  
**Folder Utama:** `quick_tutorial/`  

---

# 01 — Single-File Web Applications

Folder:
[https://github.com/sinavarasina/tugas_pemweb_opsional_123140107/tree/main/quick_tutorial/hello_world](https://github.com/sinavarasina/tugas_pemweb_opsional_123140107/tree/main/quick_tutorial/hello_world)


**Analisis:**
Aplikasi Pyramid bisa berjalan hanya dengan satu file Python.
Routing, view, dan WSGI App ditulis langsung dalam satu berkas.
`Configurator()` mengatur route dan view, `waitress.serve()` menjalankan server.
Alur minimal: request → route → view → response.

---

# 02 — Python Packages for Pyramid Applications

Folder:
[https://github.com/sinavarasina/tugas_pemweb_opsional_123140107/tree/main/quick_tutorial/package](https://github.com/sinavarasina/tugas_pemweb_opsional_123140107/tree/main/quick_tutorial/package)


**Analisis:**
Aplikasi dipindah ke struktur package Python.
`setup.py` digunakan untuk dependency dan development mode (`pip install -e .`).
`__init__.py` menandakan package.
Kode aplikasi tetap sama, hanya cara pengorganisasiannya yang berubah.

---

# 03 — Application Configuration with .ini Files

Folder:
[https://github.com/sinavarasina/tugas_pemweb_opsional_123140107/tree/main/quick_tutorial/ini](https://github.com/sinavarasina/tugas_pemweb_opsional_123140107/tree/main/quick_tutorial/ini)


**Analisis:**
Konfigurasi dipisah ke file `.ini` dengan `paste.app_factory` → memanggil fungsi `main()`.
Aplikasi dijalankan melalui `pserve development.ini --reload`.
`.ini` mengatur server, port, logging, dan environment.

---

# 04 — Easier Development with debugtoolbar

Folder:
[https://github.com/sinavarasina/tugas_pemweb_opsional_123140107/tree/main/quick_tutorial/debugtoolbar](https://github.com/sinavarasina/tugas_pemweb_opsional_123140107/tree/main/quick_tutorial/debugtoolbar)


**Analisis:**
`pyramid_debugtoolbar` ditambahkan melalui extras `[dev]`.
Aktivasi di `.ini` melalui `pyramid.includes`.
Menampilkan debugging panel berisi request, response, traceback, dan environment.

---

# 05 — Unit Tests and pytest

Folder:
[https://github.com/sinavarasina/tugas_pemweb_opsional_123140107/tree/main/quick_tutorial/unit_testing](https://github.com/sinavarasina/tugas_pemweb_opsional_123140107/tree/main/quick_tutorial/unit_testing)


**Analisis:**
Unit test memakai `pytest` dan `pyramid.testing`.
`DummyRequest()` mensimulasikan request.
Test memeriksa status code dan data response view.
Testing dilakukan tanpa server, hanya fungsi view.

---

# 06 — Functional Testing with WebTest

Folder:
[https://github.com/sinavarasina/tugas_pemweb_opsional_123140107/tree/main/quick_tutorial/functional_testing](https://github.com/sinavarasina/tugas_pemweb_opsional_123140107/tree/main/quick_tutorial/functional_testing)


**Analisis:**
WebTest mensimulasikan HTTP end-to-end tanpa menjalankan server sungguhan.
`TestApp(app)` memanggil view melalui WSGI app untuk memeriksa HTML final.
Functional test melengkapi unit test karena memvalidasi output sebenarnya.

---

# 07 — Basic Web Handling With Views

Folder:
[https://github.com/sinavarasina/tugas_pemweb_opsional_123140107/tree/main/quick_tutorial/views](https://github.com/sinavarasina/tugas_pemweb_opsional_123140107/tree/main/quick_tutorial/views)


**Analisis:**
View dipindah ke file `views.py`.
Dekorator `@view_config` digunakan untuk deklarasi view.
`config.scan('.views')` otomatis mendaftarkan seluruh view.
Dua view saling mengarah via hyperlink.

---

# 08 — HTML Generation With Templating

Folder:
[https://github.com/sinavarasina/tugas_pemweb_opsional_123140107/tree/main/quick_tutorial/templating](https://github.com/sinavarasina/tugas_pemweb_opsional_123140107/tree/main/quick_tutorial/templating)


**Analisis:**
Template digenerate melalui `pyramid_chameleon`.
Renderer ditentukan dengan `renderer='home.pt'`.
View hanya mengembalikan dictionary data, HTML dirender dari template.
Pengujian fokus pada data untuk unit test dan HTML untuk functional test.

---

# 09 — Organizing Views With View Classes

Folder:
[https://github.com/sinavarasina/tugas_pemweb_opsional_123140107/tree/main/quick_tutorial/view_classes](https://github.com/sinavarasina/tugas_pemweb_opsional_123140107/tree/main/quick_tutorial/view_classes)


**Analisis:**
Beberapa view digabung dalam satu class menggunakan `@view_defaults`.
`self.request` menyimpan request per-instance untuk berbagi state.
Testing perlu membuat instance class sebelum memanggil metode view.
Konfigurasi lebih rapi dan reusable dibanding fungsi terpisah.

---

# 10 — Handling Web Requests and Responses

Folder:
[https://github.com/sinavarasina/tugas_pemweb_opsional_123140107/tree/main/quick_tutorial/request_response](https://github.com/sinavarasina/tugas_pemweb_opsional_123140107/tree/main/quick_tutorial/request_response)


**Analisis:**
Pyramid menggunakan WebOb sebagai dasar request & response.
Redirect dilakukan memakai `HTTPFound`.
Parameter query didapat dari `request.params`.
Testing memeriksa redirect dan response body untuk berbagai kondisi.

---

# 11 — Dispatching URLs To Views With Routing

Folder:
[https://github.com/sinavarasina/tugas_pemweb_opsional_123140107/tree/main/quick_tutorial/routing](https://github.com/sinavarasina/tugas_pemweb_opsional_123140107/tree/main/quick_tutorial/routing)


**Analisis:**
Route menerima *replacement pattern* seperti `{first}/{last}`.
Nilai pattern tersedia di `request.matchdict`.
View memakai nilai itu dan meneruskannya ke template.
Unit test memberi nilai ke `matchdict`, functional test menggunakan URL langsung.

---

