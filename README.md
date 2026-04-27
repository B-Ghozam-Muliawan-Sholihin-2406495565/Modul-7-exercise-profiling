# JMETER GUI
## all-student-name
![1](/assets/images/all-student-name/table.png) 
![2](/assets/images/all-student-name/graph.png) 
![3](/assets/images/all-student-name/summary.png) 
![4](/assets/images/all-student-name/tree.png) 

## highest-gpa
![1](/assets/images/highest-gpa/table.png) 
![2](/assets/images/highest-gpa/graph.png) 
![3](/assets/images/highest-gpa/summary.png) 
![4](/assets/images/highest-gpa/tree.png) 

# JMETER CLI
![1](/assets/images/all-student-name/cli.png) 
![2](/assets/images/highest-gpa/cli.png) 

# Kesimpulan
- Performance pada load testing atau jmeter bertambah, terutama pada sample time setelah performance optimization. Jadi kesimpulannya aplikasi JMeter sangat berguna untuk dijadikan metrik sebagaimana baiknya aplikasi yang sudah kita buat. Jika metrik dari JMeter lebih lambat dari yang seharusnya berarti masih ada kode yang masih inefisien dalam aplikasi kita, dalam konteks modul ini banyak service call yang boros dan redundan. Hal ini membuktikan bahwa inefisiensi pada level kode, meskipun terlihat kecil, dapat berdampak besar ketika dihadapkan pada banyak concurrent user.

# Reflections
1. **What is the difference between the approach of performance testing with JMeter and profiling with IntelliJ Profiler in the context of optimizing application performance?** <br>
- JMeter bisa digunakan secara blackbox dan memiliki metrik Response Time, Throughput yang bisa dipakai untuk mendeteksi masalah yang ada di aplikasi kita saat dihadapkan oleh banyak concurrent user. Sedangkan IntelliJProfiler hanya bisa digunakan secara whitebox, dimana hanya kita sebagai developer yang bisa memakai dan dapat digunakan untuk menganalisis masalah yang sudah dideteksi oleh JMeter tadi walaupun bisa digunakan secara independen. Profiler ini memiliki metrik method CPU Time, memory allocation, thread activity dan lain-lain. Jadi kesimpulannya JMeter kita gunakan untuk mencari potensi masalah, dan Profiler kita gunakan untuk menganalisis lebih dalam masalah tersebut pada internal aplikasi kita. 
2. **How does the profiling process help you in identifying and understanding the weak points in your application?** <br>
- Profiling dapat membantu saya untuk menemukan method atau bagian kode mana yang membuat bottleneck aplikasi atau suatu aktivitas dalam aplikasi kita. Profiling menyajikan performa aplikasi saat dijalankan, sehingga kita bisa mengetahui method mana yang mengambil resource terlalu banyak dari biasanya agar bisa diperbaiki dan dioptimalisasi.
3. **Do you think IntelliJ Profiler is effective in assisting you to analyze and identify bottlenecks in your application code?** <br>
- Menurut saya IntelliJ Profiler efektif untuk menganalisis dan mengidentifikasi bottleneck, karena profiler ini memberikan karena menyediakan flame graph dan call tree yang memudahkan saya melihat method mana yang paling banyak konsumsi CPU time. Selain itu, profiler juga menunjukkan jumlah pemanggilan per method, sehingga saya langsung bisa identifikasi mana yang dipanggil tidak wajar.
4. **What are the main challenges you face when conducting performance testing and profiling, and how do you overcome these challenges?** <br>
- Tantangan utama saya adalah menginterpretasikan hasil profiling, khususnya saat membaca flame graph dan call tree. Flame graph tidak hanya menampilkan method dari kode kita sendiri, tetapi juga method dari library eksternal, sehingga saya harus teliti dalam memisahkan mana yang benar-benar bottleneck dari kode kita dan mana yang merupakan behavior normal dari library. Untuk mengatasinya, saya mempelajari hasil profiling secara bertahap sambil menghubungkannya langsung dengan kode yang ada, serta mencari referensi dari google atau dokumentasi ketika menemukan sesuatu yang belum familiar.
5. **What are the main benefits you gain from using IntelliJ Profiler for profiling your application code?** <br>
- Menurut saya, manfaat dari IntelliJ Profiler adalah kemampuannya untuk menampilkan secara visual, method mana yang paling banyak mengonsumsi CPU time melalui flame graph dan call tree. Selain itu, profiler juga menunjukkan jumlah pemanggilan per method, sehingga saya bisa langsung mengidentifikasi anomali yang tidak terlihat hanya dari membaca kode. Secara keseluruhan, IntelliJ Profiler membantu saya berpindah dari sekadar menebak-nebak apa penyebab masalah menjadi menemukan bottleneck secara tepat dan mudah melalui data dari aplikasi kita.
6. **How do you handle situations where the results from profiling with IntelliJ Profiler are not entirely consistent with findings from performance testing using JMeter?** <br>
- Pertama-tama saya harus menganalisis dulu kenapa hal itu terjadi, karena hal tersebut bisa terjadi kalau semisal load testing JMeter dilakukan pada web yang sudah di deploy, sedangkan Profiler dijalankan saat program di run secara local. Jadi perbedaan bisa terjadi karena faktor eksternal network latency atau konfigurasi environment yang tidak sama. Jadi solusinya adalah menjalankan ulang profiling dan testing JMeter secara local dan independen (tidak dilakukan secara bersamaan) agar environment lebih terkontrol serta meminimalkan adanya ketidak konsistenan. Namun sejauh ini profiler dan JMeter masih konsisten dalam hasilnya.
7. **What strategies do you implement in optimizing application code after analyzing results from performance testing and profiling? How do you ensure the changes you make do not affect the application's functionality?** <br>
- Setelah menganalisis hasil profiling dan load testing, strategi saya adalah memindahkan logika yang seharusnya dikerjakan database kembali ke database, mengganti filtering di Java dengan query langsung ke DB, dan menghindari pembuatan object yang redundant. Untuk memastikan fungsi aplikasi tetap sama, saya menjalankan ulang aplikasi dan memverifikasi secara manual, namun optimalnya dilakukan dengan menjalankan unit-test serta fungsional test agar testing ter-otomasi dan lebih konsisten.
