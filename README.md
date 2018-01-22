# Welcome to Standarizing of angular 5 aspnetzero framework
Didalam framework ini sudah dibuatkan contoh-contoh koding seperti upload image, datatable, shared component, get param url, dsb yang bisa langsung dipakai dan sudah distandarkan beberapa hal demi kemudahan dan efektivitas dengan harapan pengguna selalu menggunakan standar ini. 

Framework yang terdapat disini berasal dari [aspnetzero](https://www.aspnetzero.com) yang sudah diupdate dan diperbaiki. Dokumentasi lebih detail yang tidak terdapat disini dapat dilihat di [dokumentasi asli aspnetzero](https://www.aspnetzero.com/Documents).
***
## 1. Generate Service Proxy
Buka CMD dan masuk ke folder **./nswag**. Jalankan file **refresh.bat** untuk re-generate service proxy class (digunakan untuk memanggil method-method service/api/backend).

Saat ada penambahan service baru, kita harus mendaftarkannya di **src/shared/service-proxies/service-proxy.module.ts**. Buka dan tambahkan **ApiServiceProxies.NewServiceNameServiceProxy** pada array providers.
Langkah kedua ini hanya diperlukan saat ada service baru ditambahkan, jika hanya ada perubahan pada service yang sudah pernah didaftarkan maka tidak perlu dilakukan lagi.
