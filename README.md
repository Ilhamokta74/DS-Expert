# Proyek Akhir: Menyelesaikan Permasalahan Perusahaan Edutech

<img src="https://raw.githubusercontent.com/AbiyaMakruf/Dicoding-MenyelesaikanPermasalahanHumanResources/main/images/nilai.png" width="500">

Kriteria tambahan yang saya kerjakan sehingga mendapat nilai terbaik:
1. Memberikan beberapa rekomendasi action items untuk yang dapat diikuti oleh perusahaan untuk mencapai target mereka.
2. Membuat visualisasi data yang baik dan efektif dengan menerapkan prinsip desain dan integritas.
3. Membuat model machine learning untuk membantu departemen HR. Pastikan Anda membuat script Python sederhana untuk menjalankan proses prediksi.

Kriteria tambahan yang tidak saya kerjakan:
1. Membuat video singkat (maksimal 5 menit). Video tersebut harus menjelaskan beberapa poin berikut.
    - Menjelaskan business dashboard yang telah dibuat.
    - Menjelaskan kesimpulan atau conclusion dari dashboard tersebut.

## Business Understanding
Jaya Jaya Maju merupakan perusahaan multinasional yang berdiri sejak tahun 2000, dengan lebih dari 1000 karyawan yang tersebar di seluruh negeri. Meskipun perusahaan ini telah berkembang menjadi cukup besar, mereka masih menghadapi tantangan signifikan dalam mengelola karyawannya. Salah satu dampak utama dari tantangan ini adalah tingginya *attrition rate*, yaitu rasio jumlah karyawan yang keluar dengan total karyawan keseluruhan, yang mencapai lebih dari 10%. Tingginya *attrition rate* ini mengindikasikan adanya masalah dalam mempertahankan karyawan, yang dapat berdampak negatif pada produktivitas, biaya rekrutmen, dan stabilitas operasional perusahaan.

### Permasalahan Bisnis

1. Seberapa tinggi tingkat attrition di perusahaan ini?
2. Faktor-faktor apa saja yang mempengaruhi keputusan karyawan untuk meninggalkan perusahaan?
3. Apakah ada perbedaan tingkat attrition berdasarkan role atau departemen tertentu di perusahaan?
4. Bagaimana pengaruh lembur (overtime) terhadap keputusan karyawan untuk keluar dari perusahaan?

### Cakupan Proyek

* Analisis Data: Menggunakan data karyawan yang ada untuk mengidentifikasi faktor-faktor utama yang mempengaruhi attrition.
* Visualisasi & Pelaporan: Mengembangkan dashboard bisnis yang dapat digunakan oleh manajer HR untuk memonitor dan menganalisis faktor-faktor tersebut secara visual.
* Rekomendasi & Intervensi: Berdasarkan hasil analisis, memberikan rekomendasi untuk intervensi yang dapat dilakukan untuk mengurangi attrition rate dan meningkatkan kepuasan karyawan.

### Persiapan

Sumber data: dataset yang digunakan merupakan dataset [Jaya Jaya Maju](https://github.com/dicodingacademy/dicoding_dataset/tree/main/employee).

* Setup conda environment:

    ```
    conda create --name proyek-human-resources python==3.9.15
    ```
* Install requirements:
    ```
    pip install -r requirements.txt
    ```
* Setup metabase:
    ```
    docker pull metabase/metabase:v0.46.4
    docker run -p 3000:3000 --name metabase metabase/metabase
    ```
    Akses metabase pada http://localhost:3000/setup dan lakukan setup.
* Setup database (supabase):

    * Buat akun dan login https://supabase.com/dashboard/sign-in.
    * Buat new project
    * Copy URI pada database setting
    * Kirim dataset menggunakan sqlalchemy 
    ```python
    from sqlalchemy import create_engine
 
    URL = "DATABASE_URL"
    
    engine = create_engine(URL)
    df.to_sql('orders', engine)
    ```

## Business Dashboard

Dashboard ini dirancang untuk memberikan wawasan komprehensif kepada tim HR mengenai faktor-faktor yang berkontribusi terhadap keputusan karyawan untuk meninggalkan perusahaan. Dengan dashboard ini, tim HR dapat:

- Mengidentifikasi area atau departemen yang memiliki tingkat attrition tinggi.
- Menganalisis faktor-faktor seperti lembur, kepuasan kerja, dan kelompok demografis yang mungkin mempengaruhi attrition.
- Mengambil tindakan proaktif untuk meningkatkan retensi karyawan dan mengurangi biaya terkait dengan pergantian karyawan.

    <img src="https://raw.githubusercontent.com/AbiyaMakruf/Dicoding-MenyelesaikanPermasalahanHumanResources/main/images/dashboard.jpg">

## Conclusion

1. Seberapa tinggi tingkat attrition di perusahaan ini?
    * Jawaban: Tingkat attrition di perusahaan ini adalah sekitar 17%. Ini berarti bahwa satu dari enam karyawan meninggalkan perusahaan dalam jangka waktu tertentu, menunjukkan bahwa tingkat keluar karyawan cukup signifikan.

    <img src="https://raw.githubusercontent.com/AbiyaMakruf/Dicoding-MenyelesaikanPermasalahanHumanResources/main/images/attrition.png" width="500">

2. Faktor-faktor apa saja yang mempengaruhi keputusan karyawan untuk meninggalkan perusahaan?
    * Jawaban: Beberapa faktor utama yang mempengaruhi keputusan karyawan untuk meninggalkan perusahaan meliputi:
        * Lembur (Overtime): Karyawan yang sering bekerja lembur cenderung memiliki kemungkinan lebih tinggi untuk keluar dari perusahaan.
        * Status Perkawinan: Karyawan yang belum menikah (single) menunjukkan tingkat attrition yang lebih tinggi, yang mungkin mencerminkan mobilitas yang lebih besar dan keinginan untuk mencari peluang baru.

    <img src="https://raw.githubusercontent.com/AbiyaMakruf/Dicoding-MenyelesaikanPermasalahanHumanResources/main/images/faktor_attrition.png" width="500">

3. Apakah ada perbedaan tingkat attrition berdasarkan role atau departemen tertentu di perusahaan?
    * Jawaban: Ya, terdapat perbedaan tingkat attrition berdasarkan role dan departemen. Misalnya, role seperti Sales Representative dan departemen seperti Sales menunjukkan tingkat attrition yang lebih tinggi dibandingkan role atau departemen lain. Hal ini menunjukkan bahwa beban kerja, tekanan, dan mungkin juga struktur kompensasi di departemen-departemen ini dapat berkontribusi pada keputusan karyawan untuk meninggalkan perusahaan.

    <img src="https://raw.githubusercontent.com/AbiyaMakruf/Dicoding-MenyelesaikanPermasalahanHumanResources/main/images/attrition_vs_jobrole.png" width="500">
    <img src="https://raw.githubusercontent.com/AbiyaMakruf/Dicoding-MenyelesaikanPermasalahanHumanResources/main/images/attrition_vs_department.png" width="500">

4. Bagaimana pengaruh lembur (overtime) terhadap keputusan karyawan untuk keluar dari perusahaan?
    * Jawaban: Lembur memiliki pengaruh signifikan terhadap keputusan karyawan untuk meninggalkan perusahaan. Data menunjukkan bahwa karyawan yang sering bekerja lembur (overtime) memiliki tingkat attrition yang lebih tinggi. Ini mungkin terkait dengan tingkat stres yang lebih tinggi dan ketidakseimbangan antara kehidupan kerja dan pribadi.
    
    <img src="https://raw.githubusercontent.com/AbiyaMakruf/Dicoding-MenyelesaikanPermasalahanHumanResources/main/images/attrition_vs_overtime.png" width="500">


### Rekomendasi Action Items

Berikan beberapa rekomendasi action items yang harus dilakukan perusahaan guna menyelesaikan permasalahan atau mencapai target mereka.

1. Mengelola dan Mengurangi Lembur:
    * Evaluasi dan sesuaikan beban kerja untuk mengurangi lembur berlebih yang dapat mempengaruhi keseimbangan kehidupan kerja dan meningkatkan tingkat attrition.
2. Meningkatkan Kepuasan Kerja dan Lingkungan Kerja:
    * Implementasikan program peningkatan kepuasan kerja dan ciptakan lingkungan kerja yang lebih mendukung untuk menjaga keterlibatan dan retensi karyawan.
3. Strategi Retensi di Departemen Kritis:
    * Fokuskan upaya retensi pada departemen dan role yang menunjukkan tingkat attrition tinggi, seperti `Sales`. Program retensi yang ditargetkan dapat mencakup insentif, pengakuan, dan jalur karir yang jelas.
4. Penilaian dan Tindakan Berkelanjutan:
    * Pantau terus faktor-faktor yang mempengaruhi attrition melalui dashboard dan lakukan tindakan cepat saat masalah mulai muncul.

Dengan mengikuti rekomendasi ini, perusahaan diharapkan dapat menurunkan tingkat attrition, meningkatkan retensi karyawan, dan memperkuat stabilitas serta efisiensi operasional secara keseluruhan.


Username: root@mail.com
Password: root123