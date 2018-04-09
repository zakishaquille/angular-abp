# Welcome to Standarizing of Angular 5 framework
Didalam framework ini sudah dibuatkan contoh-contoh koding seperti upload image, datatable, shared component, get param url, dsb yang bisa langsung dipakai dan sudah distandarkan beberapa hal demi kemudahan dan efektivitas dengan harapan pengguna selalu menggunakan standar ini. 

Framework yang terdapat disini berasal dari [aspnetzero](https://www.aspnetzero.com) yang sudah ditambah dan diperbaiki. Dokumentasi mengenai framework ini yang tidak terdapat disini dapat dilihat di [dokumentasi asli aspnetzero](https://www.aspnetzero.com/Documents).

***

## 1. Generate Service Proxy
- Service proxy, kumpulan method http request ke API(backend), merupakan hasil generate.

- Untuk konfigurasi link API dan hasil generate service proxy dapat diedit di file **nswag/service.config.nswag**
```
"swaggerGenerator": {
    "fromSwagger": {
        "url": "http://link-api-aplikasi/swagger/v1/swagger.json",
        "output": null
    }
  },
```

- Saat ada penambahan service baru, kita harus mendaftarkannya di **src/shared/service-proxies/service-proxy.module.ts** pada array providers
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
> Langkah kedua ini hanya diperlukan saat ada service baru ditambahkan, jika hanya ada perubahan pada service yang sudah pernah didaftarkan maka tidak perlu dilakukan lagi.
