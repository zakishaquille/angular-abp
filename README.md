# Welcome to Standarizing of Angular 5 Framework
Didalam framework ini sudah dibuatkan contoh-contoh koding seperti upload image, datatable, shared component, get param url, dsb yang bisa langsung dipakai dan sudah distandarkan beberapa hal demi kemudahan dan efektivitas. 

Framework yang terdapat disini berasal dari [aspnetzero](https://www.aspnetzero.com) yang sudah ditambah dan diperbaiki. Dokumentasi lebih dalam mengenai framework ini dapat dilihat di [dokumentasi asli aspnetzero](https://www.aspnetzero.com/Documents).

***

> Jalankan `npm install` dan `yarn install` setelah clone project untuk menginstall package-package project agar dapat di-run.

## I. Generate Service Proxy
- *Service proxy*, kumpulan method http request ke API(backend) dan merupakan hasil generate.

- Hasil generate dapat dilihat di **src/shared/service-proxies/service-proxies.ts**

- Untuk konfigurasi link API dan hasil generate service proxy dapat diedit di **nswag/service.config.nswag**
```
"swaggerGenerator": {
    "fromSwagger": {
        "url": "http://link-api-aplikasi/swagger/v1/swagger.json",
        "output": null
    }
  },
```

### Registering Service Module
- Saat ada penambahan service baru, kita harus mendaftarkannya di **src/shared/service-proxies/service-proxy.module.ts** pada array providers.
```typescript
@NgModule({
    providers: [
        ApiServiceProxies.AuditLogServiceProxy,
        ApiServiceProxies.CachingServiceProxy,
        ...,
        ApiServiceProxies.NamaServiceBaruServiceProxy
    ]
})
```
    Langkah ini hanya diperlukan saat ada class service(file) baru ditambahkan, jika hanya ada perubahan pada service yang sudah pernah didaftarkan maka tidak perlu dilakukan lagi.

## II. Shared Component/Directive
- *Shared component*, suatu komponen yang dipecah menjadi bagian sendiri agar dapat digunakan dibeberapa tempat sekaligus. 
Contoh: dropdown negara, form sign up, pesan error validasi form.

- *Directive*, suatu class terpisah yang digunakan untuk menerapkan sesuatu ke komponen yang menggunakannya. 
Contoh: datepicker, masking phone number input, format currency.

- Maintenance lebih mudah karena jika ada perubahan hanya merubah 1 code untuk beberapa page yang menggunakannya.

- File-file shared berada di **src/app/main/share/**

- Buat file shared untuk page masing-masing di **src/app/main/share/[nama-module]/**

### 1. Input Dropdown
#### Base DDL Version
- Component ini me-extend class `BaseDropDownListComponent` di file **src/app/main/share/base-ddl.component.ts**
- Contoh yg service tanpa parameter di **src/app/main/share/rnd/example-ddl.component.ts**
- Contoh yg service dengan parameter di **src/app/main/share/rnd/example-lang-ddl.component.ts**

Params:
Nama            | Place     | Type          | Nilai default     | Fungsi
----------------|-----------|---------------|-------------------|------------------------------------
input           | HTML/TS   | String/Array  |                   | Untuk parameter request service. Gunakan array jika parameter lebih dari satu
isDisabled      | HTML/TS   | boolean       | false             | Untuk men-disable dropdown
emptyValueText  | HTML/TS   | String        | Nothing Selected  | Nilai yang tampil saat value kosong
labelField      | TS        | String/Array  |                   | Key field json yg ditampilkan. Jika array maka ditampilkan dengan separator dash( - ). Misal: "Adams - Manager"
valueField      | TS        | String/Array  |                   | Key field json sebagai value. Jika array maka disimpan dengan separator pipe( \| ). Misal: "Adams\|Manager"
listResult      | TS        | any           |                   | Service get data dropdown

#### Custom DDL Version
- Gunakan versi ini saat hasil request service masih perlu diolah atau data tidak persis dibawah key result/result.items pada json
- Contoh di **src/app/main/share/rnd/example-complex-ddl.component.ts**