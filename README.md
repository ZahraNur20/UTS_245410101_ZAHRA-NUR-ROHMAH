# UTS_245410101_ZAHRA-NUR-ROHMAH

# JAWABAN UTS

# **SOAL 1 :  Jelaskan teorema CAP dan BASE dan keterkaitan keduanya. Jelaskan menggunakan contoh yang pernah anda gunakan.**

1. Teorema CAP (Consistency, Availability, Partition Tolerance)
   Teorema CAP menyatakan bahwa dalam sistem terdistribusi, Anda hanya dapat menjamin dua dari tiga properti berikut secara bersamaan:
   
   a. Consistency : Semua node melihat data yang sama pada saat yang sama (data terbaru).

   b. Availability :  Sistem selalu merespons request (tidak ada downtime).

   c. Partition Tolerance : Sistem tetap beroperasi meskipun ada kegagalan komunikasi antar node (partisi jaringan).

   # Contoh
   
   Ketika aku memesan makanan lewat GoFood atau GrabFood di daerah dengan sinyal yang lemah, sebenarnya sistem di belakang layar sedang menjalankan prinsip CAP. Meskipun koneksi internetku sering putus-nyambung, aplikasi tetap berusaha bisa dibuka dan digunakan ini menunjukkan Availability, karena sistem selalu merespons meski kualitas jaringan buruk. Di sisi lain, karena server atau node yang menyimpan data harga, promo, dan menu tersebar di beberapa lokasi berbeda, terkadang ada Partition atau gangguan komunikasi antar node tersebut. Agar aplikasi tetap bisa digunakan, sistem memilih untuk tetap beroperasi meskipun data belum sepenuhnya sinkron. Akibatnya, beberapa informasi seperti harga terbaru atau promo tidak langsung muncul di sini Consistency dikorbankan. Jadi cara kerjanya adalah: selama koneksi antar node terganggu, aplikasi tetap memberikan data yang tersedia saat itu, lalu akan memperbaruinya ketika jaringan stabil dan sinkronisasi berhasil. Dengan demikian, pengguna tetap bisa memesan makanan tanpa harus menunggu data konsisten 100% di semua server.
   
3. Teorema BASE (Basically Available, Soft State, Eventually Consistent)
   BASE adalah filosofi desain untuk sistem yang memilih jalur AP (Ketersediaan) dari trade-off CAP. Ini berfokus pada konsistensi yang longgar dari waktu ke waktu:

   a. Basically Available: Menjamin ketersediaan tinggi (filosofi A dari CAP).

   b. Soft State: Status data dapat berubah seiring waktu (tidak fixed), karena konsistensi masih menyebar.

   c. Eventually Consistent: Sistem menjamin data akan konsisten di semua node pada akhirnya, setelah traffic berhenti atau partisi pulih.

   # Contoh

   Ketika aku mengunggah foto di Instagram, sistem bekerja dengan pendekatan BASE agar aplikasi tetap responsif. Begitu foto aku upload, Instagram langsung menampilkannya di profil meskipun proses penyimpanan dan penyebaran datanya ke banyak server di seluruh dunia belum selesai hal ini menunjukkan Basically Available, karena fitur tetap bisa dipakai tanpa menunggu semua server sinkron. Setelah itu, sering kali caption, jumlah like, atau komentar tidak langsung muncul atau berubah-ubah; kondisi ini disebut Soft State, sebab data masih dalam proses penyebaran antar server dan belum mencapai keadaan stabil. Beberapa saat kemudian, ketika proses sinkronisasi antar node selesai dan jaringan kembali normal, semua data seperti jumlah like, komentar, dan caption akhirnya seragam di semua server ini yang disebut Eventually Consistent. Dengan cara kerja seperti ini, Instagram memastikan penggunanya bisa tetap menggunakan aplikasi dengan lancar, sementara konsistensi data diperbarui secara bertahap di belakang layar.
   
# **SOAL 2 : Jelaskan keterkaitan antara GraphQL dengan komunikasi antar proses pada sistem terdistribusi. Buat diagramnya.**

Dalam sistem terdistribusi, komunikasi antar proses menjadi sangat penting karena setiap layanan biasanya berjalan terpisah. Di sini GraphQL memiliki peran besar sebagai penghubung, bukan pengganti. Jadi, GraphQL aku anggap sebagai gerbang utama tempat client mengirim permintaan, lalu GraphQL meneruskannya ke berbagai layanan di belakang layar.

Ketika client mengirim query, GraphQL tidak mengambil data sendirian. GraphQL akan memecah permintaan itu menjadi beberapa panggilan antar proses (inter-process communication / IPC) seperti REST, gRPC, atau message queue ke microservices yang relevan. Setelah semua service memberikan respons, GraphQL menggabungkannya menjadi satu data lengkap sesuai kebutuhan client.

Dengan cara ini, aku bisa bilang kalau GraphQL membuat komunikasi antar proses menjadi lebih efisien. Client tidak perlu memanggil banyak endpoint; cukup satu query, dan GraphQL yang mengatur koordinasi antar prosesnya. Ini mengurangi over-fetching, under-fetching, dan menurunkan beban komunikasi dalam sistem terdistribusi.
