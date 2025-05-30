**Nama**: Alyssa Layla Sasti  <br /> 
**Kelas**: AdPro B  <br />
**NPM**: 2306152052 <br />

# REFLECTION MODULE 11 KUBERNETES
## Reflection on Hello Minikube
- Sebelum Expose
![sebelumexpose](images/sebelumexpose.jpg)
- Setelah Expose
![setelahexpose](images/setelahexpose.jpg)

1. Compare the application logs before and after you exposed it as a Service. Try to open the app several times while the proxy into the Service is running. What do you see in the logs? Does the number of logs increase each time you open the app?
- Sebelum saya mengekspos aplikasi sebagai sebuah Service, log yang ditampilkan dari kubectl logs hanya menunjukkan bahwa server HTTP dan UDP berhasil dijalankan. Tidak ada aktivitas lain yang terlihat karena tidak ada request yang masuk ke dalam aplikasi. Namun, setelah saya mengekspos Deployment menggunakan kubectl expose dan menjalankan minikube service hello-node, saya bisa membuka aplikasi dari browser melalui alamat lokal yang disediakan (misalnya http://127.0.0.1:XXXX). Setiap kali saya membuka aplikasi tersebut di browser, saya melihat bahwa jumlah log di terminal bertambah. Log menunjukkan aktivitas permintaan HTTP yang masuk ke aplikasi. Ini membuktikan bahwa aplikasi memang menerima request dari luar setelah diekspos sebagai Service. Dengan kata lain, setiap interaksi saya dari browser menghasilkan tambahan entri di log aplikasi.

2. Notice that there are two versions of `kubectl get` invocation during this tutorial section. The first does not have any option, while the latter has `-n` option with value set to
`kube-system`. What is the purpose of the `-n` option and why did the output not list the pods/services that you explicitly created
- Dalam tutorial, saya menemukan bahwa ada dua bentuk perintah kubectl get yang digunakan: satu tanpa opsi tambahan, dan satu lagi dengan opsi -n kube-system. Opsi -n digunakan untuk menyaring namespace tertentu, dalam hal ini kube-system yang merupakan namespace khusus untuk komponen internal Kubernetes (seperti metrics-server, coredns, dan sebagainya).
- Resource seperti Deployment dan Service yang saya buat dengan kubectl create deployment dan kubectl expose secara default berada di namespace default, bukan kube-system. Oleh karena itu, ketika saya menjalankan kubectl get pods -n kube-system, tidak ada resource hello-node di situ. Hal ini menunjukkan pentingnya memahami namespace dalam Kubernetes agar bisa mengakses dan memonitor resource yang sesuai.