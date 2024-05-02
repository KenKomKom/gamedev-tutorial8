Apa saja hal-hal positif yang kamu identifikasi dari pengalaman para pemain ketika mencoba game kelompok?

Pemain merasakan suasana menyeramkan dari permainan walaupun belum ada implementasi audio maupun dialogue di gamenya. Selain itu, gamenya sendiri cukup mudah untuk diselesaikan oleh pemain saat pemain sudah memahami target untuk melanjutkan progresi di game.

Apa saja hal-hal negatif (atau, pain points) yang kamu identifikasi dari pengalaman para pemain ketika mencoba game kelompok?

Masih terdapat banyak bug dalam gamenya. Selain itu, text yang muncul sulit dibaca oleh pemain karena kurng kontras. Pemain juga merasa kalau tujuan tiap level tidak dijelaskan dengan baik sehingga pemain biasa menunggu arahan dari moderator atau mondar mandir di level tersebut. Pemain juga merasa diperlukannya tutorial untuk mempermudah pembelajaran awal.

Dari feedback-feedback yang telah diperoleh, apakah ada isu yang terkait pencapaian kondisi flow oleh pemain?

Ada, banyak pemain merasa kalau tujuan permainan tidak jelas sehingga pemain sulit untuk masuk ke flow. Namun, mini game yang ada di dalam gamenya sendiri cukup mudah dan menantang untuk pemain.

Misalnya, apakah ada tantangan di dalam game yang masih kurang tepat dengan kemampuan pemain pada level tertentu?

Tidak menurut saya, tiap tantangan yang dibuat kebanyakan pemain yang mencobanya merasa lumayan seru.

Atau, apakah ada rancangan level di dalam game yang dirasa terlalu membosankan bagi pemain?

Pemain-pemain yang memainkan pada beta-testing sejauh ini, tidak merasa kebosanan saat memainkannya mungkin karena permainannya cukup singkat juga.

Dari jawaban kamu terhadap pertanyaan 1 hingga 3, tuliskan secara singkat, dalam bentuk bullet points, apa saja hal yang ingin kamu polish dan balance?

Yang ingin di-polish: penambahan fog of war pada tiap level. Penambahan asset audio sehingga lebih terasa menyeramkan. Mini game yang terdapat musuh karena musuhnya blm bisa bergerak dengan baik untuk menyerang pemain.

Yang perlu dibalance adalah jumlah stamina pemain didalam tiap level karena sepertinya 10 stamina terlalu memudahkan pemain untuk menyelesaikan level.

Untuk masing-masing poin di jawaban pertanyaan 4, jabarkan secara singkat (1 - 3 kalimat) mengenai rencana kerja kamu untuk mengimplementasikan usulan tersebut.

Polishing:

- Implementasi fog of war akan dilakukan pada camera pemain sehingga mempermurah komputasi harapannya.

- Implementasi asset audio bisa menggunakan asset gratis yang didapatkan dari internet.

- Implementasi polishing pergerakan musuh bisa menggunakan navigation layer sehingga pe-rgerakan musuh menjadi lebih pintar dan tidak stuck di tembok.

Balancing:

- Perlu dilakukan proses iteratif untuk mengetahui titik "sweet spot" stamina tiap level diperlukan seberapa banyak sehingga pemain tidak bisa boros mengganti karakter dan juga tidak merasa tidak diberikan kebebasan mengganti karakter.


### Proses pengerjaan
Jadi saya membuat particlegpu2d pada level1 dan menset-upnya sesuai dengan permintaan tutorial, dimana :
- amount : 500
- lifetime : 4
- scale : 10
- scale random : 0.5
- emission shape : box
- box extents : 2000,1,1
- Color : A9A9A9
- Gravity : (-500,500)
- Spread : 20
- Rotation degrees : 180
- local coords : off
- visibility rect : -2000, -1000, 4000, 1000
- transform.position : 1700,-200
- transform.rotation_degrees : 180
- angle : 45
- visible.show_behind_parent = true
Dan untuk trail particle pada scene player.tscn:
- emmiting : on
- amount : 4
- lifetime: 0.5
- gravity : -200
- spread : 180
- velocity : 50
- emission box :Box
- box extents : 30,1,1
- transform.y= 30
- local coords = false

dan ditambahkan kode
```
onready var particle = self.get_node("Particles2D")
...
if is_on_floor() and (Input.is_action_pressed("left") or Input.is_action_pressed("right")):
        particle.set_emitting(true)
    else:
        particle.set_emitting(false)
```
Setelah itu ditambahkan spawner.tscn pada scene level 1. Dan setelah beberapa iterasi saya menetapkan Spawn Rate-nya pada 1.3 detik dan saya juga ubah collision enemy menjadi capsule agar lebih adil.

Setelah hal-hal tersebut selesai dilanjutkan dengan pembuatan readme.md
