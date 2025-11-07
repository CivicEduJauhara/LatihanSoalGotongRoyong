<!DOCTYPE html>
<html lang="id">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Kuis Gotong Royong Kelas XII</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;600;700&display=swap" rel="stylesheet">
    <style>
        body {
            font-family: 'Inter', sans-serif;
            background-color: #f0f4f8; /* Light blue-gray background */
        }
        .container-quiz {
            max-width: 900px;
        }
        .question-card {
            box-shadow: 0 10px 25px -5px rgba(0, 0, 0, 0.1), 0 0 10px -5px rgba(0, 0, 0, 0.04);
        }
        .option-button {
            transition: all 0.3s ease;
            cursor: pointer;
        }
        .option-button:not(.disabled):hover {
            background-color: #e0f2fe; /* Lightest blue on hover */
            transform: translateY(-1px);
        }
        .correct-answer {
            background-color: #d1fae5; /* Green for correct */
            border-color: #34d399;
        }
        .incorrect-answer {
            background-color: #fee2e2; /* Red for incorrect */
            border-color: #f87171;
        }
        .selected-option {
            border: 3px solid #3b82f6; /* Blue border on selection */
        }
        .disabled {
            pointer-events: none;
            opacity: 0.8;
        }
    </style>
</head>
<body class="p-4 md:p-8">

    <div id="app" class="container-quiz mx-auto">
        <!-- Tampilan akan di-render di sini oleh JavaScript -->
    </div>

    <script>
        // Data Kuis (40 Soal Pilihan Ganda)
        const quizData = {
            title: "Kuis Gotong Royong dalam Konteks Kontemporer",
            questions: [
                // Kategori Mudah (1-10) - Low Difficulty
                {
                    questionNumber: 1,
                    category: "Mudah",
                    question: "Landasan moral Pancasila yang secara eksplisit menekankan pada kerja sama, persatuan, dan keadilan sosial, dan diwujudkan dalam Gotong Royong, terutama terdapat pada Sila ke berapa?",
                    hint: "Fokus pada Sila yang berbicara tentang persatuan dan kesatuan.",
                    imageUrl: "",
                    answerOptions: [
                        { text: "Sila Pertama dan Kedua", rationale: "Sila Pertama berfokus pada Ketuhanan, dan Sila Kedua pada Kemanusiaan yang Adil dan Beradab, kurang menekankan aspek persatuan dan kerja sama kolektif.", isCorrect: false },
                        { text: "Sila Kedua dan Keempat", rationale: "Sila Keempat berfokus pada Kerakyatan melalui permusyawaratan, yang merupakan bagian dari proses, bukan landasan utamanya.", isCorrect: false },
                        { text: "Sila Ketiga dan Kelima", rationale: "Sila Ketiga (Persatuan Indonesia) dan Sila Kelima (Keadilan Sosial) adalah inti dari semangat Gotong Royong: bersatu untuk mencapai keadilan bersama.", isCorrect: true },
                        { text: "Sila Keempat dan Kelima", rationale: "Meskipun terkait, Sila Keempat lebih fokus pada mekanisme demokrasi, sedangkan Gotong Royong adalah nilai dasarnya.", isCorrect: false },
                        { text: "Sila Pertama dan Kelima", rationale: "Sila Pertama dan Kelima memiliki fokus yang sangat berbeda. Gotong Royong lebih berakar pada aspek sosial kolektif.", isCorrect: false },
                    ]
                },
                {
                    questionNumber: 2,
                    category: "Mudah",
                    question: "Dalam konteks modern, Gotong Royong tidak lagi hanya diartikan sebagai mengangkat beban fisik. Definisi modern yang paling tepat adalah...",
                    hint: "Perhatikan kata kunci 'sumber daya' dan 'tanggung jawab' non-fisik.",
                    imageUrl: "",
                    answerOptions: [
                        { text: "Kewajiban sosial untuk membantu tetangga yang sedang kesulitan fisik.", rationale: "Ini adalah makna tradisional, bukan definisi modern yang komprehensif.", isCorrect: false },
                        { text: "Tanggung jawab kolektif untuk menanam pohon di lingkungan desa.", rationale: "Ini hanya contoh spesifik, bukan definisi umum yang luas.", isCorrect: false },
                        { text: "Berbagi ide, sumber daya non-fisik, dan tanggung jawab untuk mencapai tujuan bersama.", rationale: "Gotong Royong modern mencakup aspek intelektual dan material (sumber daya) selain fisik.", isCorrect: true },
                        { text: "Sistem barter jasa di antara anggota masyarakat yang membutuhkan.", rationale: "Barter lebih bersifat transaksional, Gotong Royong lebih bersifat sukarela dan non-transaksional.", isCorrect: false },
                        { text: "Pengumpulan dana untuk proyek pembangunan fasilitas umum.", rationale: "Ini adalah contoh spesifik dari *crowdfunding*, bukan definisi utamanya.", isCorrect: false },
                    ]
                },
                {
                    questionNumber: 3,
                    category: "Mudah",
                    question: "Salah satu tantangan utama dalam penerapan Gotong Royong di era kontemporer yang berfokus pada kepentingan diri sendiri secara berlebihan adalah...",
                    hint: "Fokus pada pola pikir yang mementingkan diri sendiri dan materi.",
                    imageUrl: "",
                    answerOptions: [
                        { text: "Ekonomi Kreatif", rationale: "Ekonomi kreatif adalah peluang, bukan tantangan, bagi Gotong Royong.", isCorrect: false },
                        { text: "Digitalisasi Kolaborasi", rationale: "Digitalisasi kolaborasi adalah peluang yang harus dimanfaatkan.", isCorrect: false },
                        { text: "Polarisasi Politik", rationale: "Polarisasi adalah tantangan, namun fokus pada kepentingan diri sendiri secara berlebihan adalah 'individualisme'.", isCorrect: false },
                        { text: "Individualisme & Hedonisme", rationale: "Fokus berlebihan pada kepentingan pribadi (individualisme) dan kesenangan materi (hedonisme) menyebabkan apatis terhadap masalah sosial.", isCorrect: true },
                        { text: "Ketahanan Bencana", rationale: "Ketahanan bencana adalah peluang untuk memperkuat Gotong Royong.", isCorrect: false },
                    ]
                },
                {
                    questionNumber: 4,
                    category: "Mudah",
                    question: "Prinsip Gotong Royong dapat menjadi peluang besar untuk mendukung program global yang berfokus pada pengentasan kemiskinan, pendidikan, dan lingkungan, yang dikenal sebagai...",
                    hint: "Ini adalah program yang dicanangkan PBB untuk pembangunan global.",
                    imageUrl: "",
                    answerOptions: [
                        { text: "AFTA (ASEAN Free Trade Area)", rationale: "AFTA adalah perjanjian ekonomi regional, bukan program pembangunan berkelanjutan global.", isCorrect: false },
                        { text: "G-20 Summit", rationale: "G-20 adalah forum kerja sama ekonomi internasional, bukan kerangka kerja pembangunan berkelanjutan.", isCorrect: false },
                        { text: "Sustainable Development Goals (SDGs)", rationale: "SDGs adalah 17 tujuan global yang sangat membutuhkan aksi kolektif dan Gotong Royong untuk implementasi lokal.", isCorrect: true },
                        { text: "NATO (North Atlantic Treaty Organization)", rationale: "NATO adalah aliansi pertahanan, tidak terkait langsung dengan pembangunan sosial dan lingkungan.", isCorrect: false },
                        { text: "MEA (Masyarakat Ekonomi ASEAN)", rationale: "MEA adalah integrasi ekonomi regional, berbeda dengan SDGs yang berfokus pada pembangunan sosial dan lingkungan.", isCorrect: false },
                    ]
                },
                {
                    questionNumber: 5,
                    category: "Mudah",
                    question: "Apa peran kunci Gotong Royong dalam menghadapi bencana alam, sesuai dengan peluang yang dianalisis dalam materi?",
                    hint: "Kata kunci 'cepat' dan 'terstruktur' dalam situasi darurat.",
                    imageUrl: "",
                    answerOptions: [
                        { text: "Menggantikan peran Badan Nasional Penanggulangan Bencana (BNPB).", rationale: "Gotong Royong melengkapi, bukan menggantikan, peran lembaga pemerintah.", isCorrect: false },
                        { text: "Menjamin semua korban mendapatkan kompensasi finansial yang adil.", rationale: "Ini adalah tugas pemerintah dan lembaga keuangan, bukan peran utama Gotong Royong.", isCorrect: false },
                        { text: "Menciptakan solidaritas cepat dan terstruktur dalam tanggap darurat dan pemulihan (resiliensi).", rationale: "Solidaritas cepat dan terstruktur adalah inti dari ketahanan bencana berbasis komunitas.", isCorrect: true },
                        { text: "Membentuk kelompok oposisi terhadap kebijakan penanganan bencana pemerintah.", rationale: "Gotong Royong seharusnya mendukung, bukan menentang, upaya penanggulangan.", isCorrect: false },
                        { text: "Menyediakan layanan hiburan dan psikologis pasca-bencana.", rationale: "Ini adalah bagian dari pemulihan, namun peran kuncinya adalah solidaritas cepat.", isCorrect: false },
                    ]
                },
                {
                    questionNumber: 6,
                    category: "Mudah",
                    question: "Berikut ini adalah komponen wajib pertama yang harus ada dalam proposal kegiatan kolaboratif untuk mengidentifikasi urgensi masalah, yaitu...",
                    hint: "Langkah pertama dalam proposal adalah menjelaskan 'mengapa' kegiatan ini perlu dilakukan.",
                    imageUrl: "",
                    answerOptions: [
                        { text: "Anggaran", rationale: "Anggaran adalah komponen pendukung yang dibuat setelah masalah diidentifikasi.", isCorrect: false },
                        { text: "Target Peserta", rationale: "Target peserta ditentukan setelah masalah dan tujuan ditetapkan.", isCorrect: false },
                        { text: "Latar Belakang (Identifikasi Masalah)", rationale: "Latar Belakang harus menjadi yang pertama untuk menjelaskan masalah, urgensi, dan relevansi proyek.", isCorrect: true },
                        { text: "Jadwal Pelaksanaan", rationale: "Jadwal adalah komponen teknis yang dibuat pada tahap akhir perancangan.", isCorrect: false },
                        { text: "Metode Kegiatan", rationale: "Metode ditentukan setelah masalah dan tujuan proyek dirumuskan.", isCorrect: false },
                    ]
                },
                {
                    questionNumber: 7,
                    category: "Mudah",
                    question: "Sifat dari tujuan kegiatan kolaboratif yang baik dan sistematis, seperti yang disinggung dalam materi, haruslah...",
                    hint: "Gunakan akronim yang memastikan tujuan spesifik, terukur, dan terikat waktu.",
                    imageUrl: "",
                    answerOptions: [
                        { text: "Idealistis, Luas, dan Berfokus Komunitas", rationale: "Ini terlalu umum, tujuan harus lebih terukur.", isCorrect: false },
                        { text: "Fleksibel, Tidak Terikat Waktu, dan Relevan", rationale: "Tujuan harus terikat waktu (Time-bound), bukan tidak terikat waktu.", isCorrect: false },
                        { text: "Ambisius, Berani, dan Inovatif", rationale: "Ini adalah kualitas proyek, bukan kriteria perumusan tujuan.", isCorrect: false },
                        { text: "SMART (Specific, Measurable, Achievable, Relevant, Time-bound)", rationale: "SMART adalah kriteria yang menjamin tujuan kegiatan Gotong Royong dapat diukur, dicapai, dan dievaluasi.", isCorrect: true },
                        { text: "Populer, Terkenal, dan Mudah Dilakukan", rationale: "Popularitas bukanlah kriteria utama bagi tujuan yang sistematis.", isCorrect: false },
                    ]
                },
                {
                    questionNumber: 8,
                    category: "Mudah",
                    question: "Pemimpin dalam kegiatan Gotong Royong modern harus berfokus pada inspirasi, koordinasi, dan pemberdayaan, bukan pada...",
                    hint: "Fokus pada cara memimpin yang otoriter atau top-down.",
                    imageUrl: "",
                    answerOptions: [
                        { text: "Motivasi", rationale: "Motivasi adalah bagian dari kepemimpinan yang baik.", isCorrect: false },
                        { text: "Komando (Memberi Perintah Mutlak)", rationale: "Gotong Royong adalah tentang partisipasi sukarela, bukan komando militeristik atau otoriter.", isCorrect: true },
                        { text: "Delegasi Tugas", rationale: "Delegasi adalah keterampilan wajib dalam kepemimpinan proyek.", isCorrect: false },
                        { text: "Manajemen Konflik", rationale: "Manajemen konflik adalah keterampilan penting yang harus dimiliki pemimpin.", isCorrect: false },
                        { text: "Akuntabilitas", rationale: "Akuntabilitas adalah tuntutan etis dalam proyek.", isCorrect: false },
                    ]
                },
                {
                    questionNumber: 9,
                    category: "Mudah",
                    question: "Penggunaan platform *crowdfunding* untuk mengumpulkan donasi bagi korban bencana alam merupakan contoh penerapan Gotong Royong dalam peluang apa?",
                    hint: "Fokus pada aspek teknologi dan pengumpulan sumber daya secara daring.",
                    imageUrl: "",
                    answerOptions: [
                        { text: "Ekonomi Kreatif Berbasis Komunitas", rationale: "Ekonomi kreatif berfokus pada produk dan UMKM, bukan donasi cepat.", isCorrect: false },
                        { text: "Mendukung Tujuan Pembangunan Berkelanjutan (SDGs)", rationale: "Meskipun mendukung, kategori yang lebih spesifik adalah digitalisasi.", isCorrect: false },
                        { text: "Digitalisasi Kolaborasi", rationale: "Platform *crowdfunding* adalah contoh utama pemanfaatan teknologi untuk mengumpulkan sumber daya secara massal (kolaborasi digital).", isCorrect: true },
                        { text: "Ketahanan Bencana (Resiliensi)", rationale: "Ini adalah konteksnya, tetapi *crowdfunding* adalah metodenya (Digitalisasi).", isCorrect: false },
                        { text: "Edukasi Berbasis Komunitas", rationale: "Ini bukan tentang edukasi, tetapi tentang pengumpulan dana.", isCorrect: false },
                    ]
                },
                {
                    questionNumber: 10,
                    category: "Mudah",
                    question: "Apa yang dimaksud dengan 'akuntabilitas' dalam konteks kepemimpinan Gotong Royong setelah kegiatan selesai?",
                    hint: "Ini terkait dengan pertanggungjawaban dan evaluasi pasca-proyek.",
                    imageUrl: "",
                    answerOptions: [
                        { text: "Membagi keuntungan finansial dari proyek secara merata.", rationale: "Akuntabilitas jarang melibatkan keuntungan finansial, kecuali dalam proyek wirausaha.", isCorrect: false },
                        { text: "Menyediakan makanan dan minuman yang cukup untuk semua relawan.", rationale: "Ini adalah bagian dari logistik, bukan akuntabilitas pasca-kegiatan.", isCorrect: false },
                        { text: "Memberikan sanksi kepada relawan yang tidak bekerja maksimal.", rationale: "Akuntabilitas berfokus pada laporan dan evaluasi, bukan sanksi.", isCorrect: false },
                        { text: "Mengumpulkan umpan balik (*feedback*), dan membuat laporan sederhana mengenai keberhasilan dan perbaikan.", rationale: "Akuntabilitas adalah pertanggungjawaban dan transparansi hasil serta proses pembelajaran.", isCorrect: true },
                        { text: "Mencari proyek baru segera setelah proyek lama selesai.", rationale: "Ini adalah inisiasi proyek baru, bukan akuntabilitas proyek yang sudah selesai.", isCorrect: false },
                    ]
                },

                // Kategori Sulit dengan Analisis (11-20) - High Difficulty
                {
                    questionNumber: 11,
                    category: "Sulit dengan Analisis",
                    question: "Mengapa polarisasi politik dan sosial dianggap sebagai tantangan Gotong Royong yang sangat signifikan di konteks nasional?",
                    hint: "Fokus pada dampak polarisasi terhadap *persatuan* dan *konsensus*.",
                    imageUrl: "",
                    answerOptions: [
                        { text: "Karena polarisasi mengurangi dana pemerintah untuk proyek sosial.", rationale: "Dampak utamanya bukan pada dana, tetapi pada kepercayaan sosial.", isCorrect: false },
                        { text: "Karena menciptakan kelompok 'kita' vs 'mereka', sehingga sulit mencapai konsensus dan mobilisasi untuk tujuan bersama.", rationale: "Gotong Royong menuntut kesatuan aksi, yang dirusak oleh pembagian masyarakat yang tajam (polarisasi).", isCorrect: true },
                        { text: "Karena semua energi masyarakat terfokus pada kampanye politik, bukan kegiatan sosial.", rationale: "Meskipun ada hubungannya, dampak fragmentasi sosial lebih signifikan daripada sekadar pengalihan fokus.", isCorrect: false },
                        { text: "Karena masyarakat menjadi terlalu kritis terhadap kinerja pemimpin proyek Gotong Royong.", rationale: "Kritik yang sehat adalah baik, tantangannya adalah perpecahan mendasar.", isCorrect: false },
                        { text: "Karena isu politik jauh lebih penting daripada isu sosial dan lingkungan.", rationale: "Pernyataan ini subjektif dan tidak akurat sebagai analisis tantangan Gotong Royong.", isCorrect: false },
                    ]
                },
                {
                    questionNumber: 12,
                    category: "Sulit dengan Analisis",
                    question: "Analisislah, mengapa gaya hidup digital (terutama penggunaan media sosial yang tidak produktif atau penyebaran *hoax*) dapat menghambat Gotong Royong nyata?",
                    hint: "Perhatikan dampak *hoax* dan fokus digital yang berlebihan terhadap *kepercayaan* dan *aksi fisik*.",
                    imageUrl: "",
                    answerOptions: [
                        { text: "Karena media sosial terlalu mahal dan tidak dapat diakses oleh semua lapisan masyarakat.", rationale: "Akses bukan masalah utamanya, melainkan kualitas interaksi dan informasi.", isCorrect: false },
                        { text: "Karena masyarakat hanya fokus pada Gotong Roy Royong virtual, melupakan aksi fisik di lapangan.", rationale: "Ini hanya sebagian kecil. Penghambatan utamanya adalah perusakan kepercayaan.", isCorrect: false },
                        { text: "Karena penyebaran *hoax* merusak kepercayaan antarkelompok, membuat mobilisasi Gotong Royong fisik sulit dilakukan karena minimnya rasa percaya.", rationale: "Kepercayaan adalah fondasi kolaborasi, yang dihancurkan oleh disinformasi dan perpecahan digital.", isCorrect: true },
                        { text: "Karena siswa kelas XII lebih suka bermain *game* daripada berpartisipasi dalam kegiatan sosial.", rationale: "Meskipun ada, ini adalah contoh individualisme, bukan alasan utama penghambatan oleh gaya hidup digital.", isCorrect: false },
                        { text: "Karena algoritma media sosial memprioritaskan Gotong Royong global daripada nasional.", rationale: "Algoritma tidak memiliki bias geografis, melainkan fokus pada *engagement*.", isCorrect: false },
                    ]
                },
                {
                    questionNumber: 13,
                    category: "Sulit dengan Analisis",
                    question: "Gotong Royong menuntut kerja sama dan persatuan. Jelaskan mengapa Gotong Royong lebih efektif dalam mendukung Tujuan Pembangunan Berkelanjutan (SDGs) daripada mekanisme persaingan pasar bebas.",
                    hint: "Fokus pada sifat SDGs yang bersifat 'publik' dan 'non-profit'.",
                    imageUrl: "",
                    answerOptions: [
                        { text: "Pasar bebas lebih cepat. Gotong Royong adalah warisan budaya yang lambat dan tidak efisien untuk SDGs yang ambisius.", rationale: "Gotong Royong dapat cepat jika terstruktur (peluang digitalisasi), dan pasar bebas tidak berfokus pada keadilan sosial.", isCorrect: false },
                        { text: "Gotong Royong berfokus pada sumber daya alam, sedangkan pasar bebas berfokus pada sumber daya manusia.", rationale: "Fokus keduanya tidak terbatas pada satu jenis sumber daya.", isCorrect: false },
                        { text: "SDGs sering kali membahas masalah *public goods* (lingkungan, kemiskinan) yang kurang diminati pasar, sehingga hanya kolaborasi non-profit (Gotong Royong) yang dapat mengatasi.", rationale: "Pasar cenderung mengabaikan masalah yang tidak menghasilkan keuntungan finansial, membuat Gotong Royong penting untuk isu sosial/lingkungan.", isCorrect: true },
                        { text: "Pasar bebas hanya berlaku di negara maju, sementara Gotong Royong berlaku di seluruh dunia.", rationale: "Pasar bebas berlaku global, tetapi motivasinya tidak sejalan dengan tujuan sosial SDGs.", isCorrect: false },
                        { text: "Gotong Royong mengandalkan bantuan asing, sementara pasar bebas mengandalkan investasi lokal.", rationale: "Pernyataan ini keliru. Gotong Royong fokus pada sumber daya lokal.", isCorrect: false },
                    ]
                },
                {
                    questionNumber: 14,
                    category: "Sulit dengan Analisis",
                    question: "Mengapa penetapan 'Anggaran' dalam proposal Gotong Royong tidak harus selalu berfokus pada dana tunai, tetapi juga sumber daya non-materiil?",
                    hint: "Pikirkan apa yang paling sering disumbangkan oleh relawan dalam Gotong Royong.",
                    imageUrl: "",
                    answerOptions: [
                        { text: "Dana tunai sangat sulit didapatkan, sehingga proposal hanya fokus pada donasi barang.", rationale: "Meskipun sulit, mengabaikan dana tunai adalah kurang tepat. Fokusnya adalah pada *jenis* kontribusi.", isCorrect: false },
                        { text: "Sumber daya non-materiil (tenaga, waktu, ide) adalah esensi Gotong Royong yang harus dihitung, karena nilai kontribusi tidak selalu berupa uang.", rationale: "Gotong Royong menghargai kontribusi waktu dan tenaga (in-kind contribution) setara dengan uang.", isCorrect: true },
                        { text: "Untuk menghindari tuntutan hukum jika terjadi penyalahgunaan dana tunai.", rationale: "Anggaran tetap harus mencantumkan dana tunai dan mekanisme pengawasannya (akuntabilitas).", isCorrect: false },
                        { text: "Sumber daya non-materiil lebih mudah dipertanggungjawabkan daripada dana tunai.", rationale: "Kedua jenis sumber daya harus dipertanggungjawabkan dengan metode yang berbeda.", isCorrect: false },
                        { text: "Dana tunai hanya digunakan untuk membeli peralatan besar, bukan untuk biaya operasional.", rationale: "Dana tunai dapat digunakan untuk segala kebutuhan proyek.", isCorrect: false },
                    ]
                },
                {
                    questionNumber: 15,
                    category: "Sulit dengan Analisis",
                    question: "Dalam konteks globalisasi, masuknya budaya yang menekankan individualisme merupakan tantangan. Jelaskan perbedaan mendasar antara *kerja sama* (Gotong Royong) dengan *transaksi* (Individualisme).",
                    hint: "Fokus pada *motivasi* dan *tujuan* dari masing-masing konsep.",
                    imageUrl: "",
                    answerOptions: [
                        { text: "Kerja sama adalah antar-pemerintah, sedangkan transaksi adalah antar-individu.", rationale: "Kerja sama dan transaksi dapat terjadi di tingkat mana pun.", isCorrect: false },
                        { text: "Kerja sama dimotivasi oleh kepentingan kolektif dan sukarela, sedangkan transaksi dimotivasi oleh keuntungan pribadi dan bersifat kontraktual.", rationale: "Ini adalah perbedaan mendasar dalam filosofi, di mana Gotong Royong tanpa pamrih dan transaksi berorientasi keuntungan.", isCorrect: true },
                        { text: "Kerja sama hanya terjadi di negara berkembang, sedangkan transaksi terjadi di negara maju.", rationale: "Kedua konsep ini terjadi secara global.", isCorrect: false },
                        { text: "Kerja sama menggunakan sumber daya fisik, sedangkan transaksi menggunakan uang.", rationale: "Kerja sama dapat melibatkan ide dan uang; transaksi dapat melibatkan barter.", isCorrect: false },
                        { text: "Kerja sama tidak memerlukan perencanaan, sementara transaksi memerlukan perencanaan yang matang.", rationale: "Kerja sama, seperti Gotong Royong, memerlukan perencanaan sistematis.", isCorrect: false },
                    ]
                },
                {
                    questionNumber: 16,
                    category: "Sulit dengan Analisis",
                    question: "Evaluasi dampak dari 'Erosi Nilai oleh Globalisasi' terhadap semangat komunal di Indonesia. Manakah yang paling terasa?",
                    hint: "Pikirkan tentang perubahan fokus dari 'kita' menjadi 'saya' di tengah masyarakat.",
                    imageUrl: "",
                    answerOptions: [
                        { text: "Peningkatan kualitas infrastruktur desa karena teknologi baru.", rationale: "Ini dampak positif globalisasi (teknologi), bukan erosi nilai.", isCorrect: false },
                        { text: "Meningkatnya rasa persaingan ketat yang menyebabkan menurunnya kepedulian masyarakat terhadap masalah non-pribadi.", rationale: "Globalisasi membawa etos persaingan pasar yang merusak fokus pada kebutuhan komunitas.", isCorrect: true },
                        { text: "Perubahan bahasa daerah menjadi bahasa Inggris sebagai bahasa utama di lingkungan keluarga.", rationale: "Ini dampak budaya, tetapi tidak sekuat erosi pada kepedulian sosial.", isCorrect: false },
                        { text: "Munculnya banyak platform *crowdfunding* untuk bantuan sosial.", rationale: "Ini adalah peluang positif (Digitalisasi Kolaborasi) dari globalisasi, bukan erosi nilai.", isCorrect: false },
                        { text: "Kesulitan dalam mendapatkan bahan pangan lokal karena impor yang murah.", rationale: "Ini adalah dampak ekonomi, bukan erosi langsung pada semangat komunal.", isCorrect: false },
                    ]
                },
                {
                    questionNumber: 17,
                    category: "Sulit dengan Analisis",
                    question: "Apa perbedaan mendasar antara tahap 'Inisiasi dan Persiapan' dan tahap 'Sosialisasi dan Mobilisasi' dalam kerangka kerja proyek Gotong Royong?",
                    hint: "Fokus pada *pelaku* dan *tujuan* utama dari masing-masing tahap.",
                    imageUrl: "",
                    answerOptions: [
                        { text: "Inisiasi berfokus pada dana, sedangkan Sosialisasi berfokus pada alat.", rationale: "Keduanya berfokus pada perencanaan dan sumber daya secara umum.", isCorrect: false },
                        { text: "Inisiasi dilakukan oleh tim inti untuk merancang proyek, sementara Sosialisasi dilakukan untuk meyakinkan dan mengajak partisipasi masyarakat umum.", rationale: "Inisiasi adalah tahap internal tim, Sosialisasi adalah tahap eksternal ke publik.", isCorrect: true },
                        { text: "Inisiasi adalah tahap pelaksanaan, sedangkan Sosialisasi adalah tahap pasca-pelaksanaan.", rationale: "Inisiasi dan Sosialisasi adalah tahap pra-pelaksanaan.", isCorrect: false },
                        { text: "Inisiasi berfokus pada masalah lingkungan, sedangkan Sosialisasi berfokus pada masalah sosial.", rationale: "Fokus masalah tidak membedakan kedua tahap ini.", isCorrect: false },
                        { text: "Inisiasi dilakukan oleh pemerintah daerah, sedangkan Sosialisasi dilakukan oleh sekolah.", rationale: "Kedua tahap ini dapat dilakukan oleh inisiator mana pun.", isCorrect: false },
                    ]
                },
                {
                    questionNumber: 18,
                    category: "Sulit dengan Analisis",
                    question: "Sebuah desa menghadapi masalah erosi lahan. Menurut Anda, mengapa pendekatan Gotong Royong berbasis komunitas (melibatkan semua warga) lebih unggul daripada menyerahkan masalah ini sepenuhnya kepada pemerintah daerah?",
                    hint: "Pikirkan tentang *keberlanjutan* dan *rasa kepemilikan*.",
                    imageUrl: "",
                    answerOptions: [
                        { text: "Pemerintah daerah tidak memiliki dana yang cukup untuk mengatasi erosi lahan.", rationale: "Pemerintah memiliki alokasi dana, tetapi *efektivitas*nya tergantung pada partisipasi.", isCorrect: false },
                        { text: "Pendekatan Gotong Royong menciptakan rasa kepemilikan dan menjamin keberlanjutan proyek dalam jangka panjang.", rationale: "Keberlanjutan dan rasa memiliki adalah kunci sukses inisiatif lokal. Warga akan menjaga hasil kerja mereka.", isCorrect: true },
                        { text: "Warga desa memiliki teknologi yang lebih canggih daripada pemerintah daerah.", rationale: "Warga desa biasanya tidak memiliki teknologi yang lebih canggih, tetapi memiliki pengetahuan lokal.", isCorrect: false },
                        { text: "Pemerintah daerah hanya fokus pada masalah sosial, bukan lingkungan.", rationale: "Pernyataan ini tidak akurat; pemerintah daerah menangani semua sektor.", isCorrect: false },
                        { text: "Melibatkan semua warga jauh lebih cepat daripada menunggu birokrasi pemerintah.", rationale: "Meskipun cepat, keunggulan utamanya adalah *keberlanjutan* dan *kualitas perawatan*.", isCorrect: false },
                    ]
                },
                {
                    questionNumber: 19,
                    category: "Sulit dengan Analisis",
                    question: "Suatu proposal kegiatan Gotong Royong mencantumkan tujuan 'Masyarakat senang dan bersih.' Analisislah, mengapa tujuan ini tidak memenuhi kriteria *SMART* yang disarankan.",
                    hint: "Fokus pada aspek *terukur* dan *spesifik* dari kriteria SMART.",
                    imageUrl: "",
                    answerOptions: [
                        { text: "Tujuan tersebut terlalu Spesifik (S) sehingga sulit dicapai (A).", rationale: "Justru tidak spesifik dan tidak terukur.", isCorrect: false },
                        { text: "Kata 'senang' dan 'bersih' tidak Terukur (M) dan tidak Spesifik (S), sehingga sulit untuk dievaluasi keberhasilannya.", rationale: "Tujuan harus menggunakan indikator yang dapat diukur (misalnya, 'mengurangi volume sampah 20%').", isCorrect: true },
                        { text: "Tujuan tersebut tidak memiliki unsur Relevan (R) dan Terikat Waktu (T).", rationale: "Mungkin relevan, tetapi kegagalan terbesarnya adalah pada M dan S.", isCorrect: false },
                        { text: "Tujuan tersebut terlalu Terikat Waktu (T) sehingga membatasi kreativitas.", rationale: "Tidak ada batasan waktu yang jelas, sehingga gagal di kriteria T.", isCorrect: false },
                        { text: "Tujuan tersebut harusnya hanya fokus pada 'bersih' tanpa melibatkan aspek 'senang'.", rationale: "Aspek 'senang' (dampak emosional) sulit diukur, sehingga harus diganti dengan indikator lain.", isCorrect: false },
                    ]
                },
                {
                    questionNumber: 20,
                    category: "Sulit dengan Analisis",
                    question: "Bagian 'Metode/Rancangan Kegiatan' dalam proposal harus mengandung aspek inovatif. Mengapa inovasi menjadi kunci bagi keberhasilan Gotong Royong dalam mengatasi isu-isu kontemporer yang kompleks?",
                    hint: "Pikirkan tentang perbedaan antara masalah tradisional dan masalah modern.",
                    imageUrl: "",
                    answerOptions: [
                        { text: "Inovasi diperlukan agar proyek mendapatkan liputan media dan menjadi viral.", rationale: "Liputan media adalah manfaat, bukan alasan utama inovasi.", isCorrect: false },
                        { text: "Isu kontemporer seperti perubahan iklim atau polarisasi membutuhkan solusi yang melampaui metode tradisional (seperti hanya membersihkan fisik).", rationale: "Inovasi menggabungkan aksi fisik dengan solusi modern (teknologi, edukasi, sistem baru) untuk mengatasi masalah yang kompleks.", isCorrect: true },
                        { text: "Inovasi membantu mengurangi biaya Gotong Royong secara keseluruhan.", rationale: "Inovasi sering kali membutuhkan investasi awal, sehingga ini tidak selalu benar.", isCorrect: false },
                        { text: "Gotong Royong tanpa inovasi dianggap melanggar prinsip Pancasila.", rationale: "Gotong Royong tradisional tetap sesuai Pancasila, tetapi kurang efektif untuk tantangan modern.", isCorrect: false },
                        { text: "Inovasi menjamin bahwa Gotong Royong dapat dilakukan tanpa partisipasi fisik masyarakat.", rationale: "Gotong Royong tetap membutuhkan partisipasi, inovasi hanya mengubah caranya.", isCorrect: false },
                    ]
                },

                // Kategori Penerapan (21-35) - Application
                {
                    questionNumber: 21,
                    category: "Penerapan",
                    question: "Anda adalah ketua kelas yang ingin mengadakan Gotong Royong membersihkan lingkungan sekolah. Teman Anda menolak karena merasa itu bukan tugasnya. Keterampilan kepemimpinan apa yang paling tepat Anda gunakan?",
                    hint: "Bagaimana cara Anda membuat teman Anda merasa penting dan termotivasi?",
                    imageUrl: "",
                    answerOptions: [
                        { text: "Manajemen Konflik", rationale: "Ini belum konflik. Ini adalah kurangnya motivasi atau kesadaran peran.", isCorrect: false },
                        { text: "Komando Mutlak", rationale: "Komando akan mematikan semangat Gotong Royong dan menyebabkan resistensi.", isCorrect: false },
                        { text: "Motivasi dan Apresiasi", rationale: "Berikan pemahaman tentang pentingnya kontribusi dan pengakuan atas perannya untuk memicu partisipasi sukarela.", isCorrect: true },
                        { text: "Akuntabilitas", rationale: "Akuntabilitas dilakukan pasca-kegiatan, bukan untuk mengatasi penolakan pra-kegiatan.", isCorrect: false },
                        { text: "Delegasi Tugas", rationale: "Delegasi akan lebih efektif setelah ia termotivasi untuk bergabung.", isCorrect: false },
                    ]
                },
                {
                    questionNumber: 22,
                    category: "Penerapan",
                    question: "Sebuah komunitas memutuskan untuk mengatasi masalah sampah liar dengan Gotong Royong. Agar proyek ini inovatif, hal yang sebaiknya mereka lakukan selain membersihkan adalah...",
                    hint: "Cari solusi yang menggabungkan aksi fisik dengan aspek edukasi atau ekonomi.",
                    imageUrl: "",
                    answerOptions: [
                        { text: "Hanya membersihkan sampah dan membuangnya ke TPA terdekat.", rationale: "Ini adalah solusi tradisional, tidak inovatif, dan tidak mengatasi akar masalah.", isCorrect: false },
                        { text: "Melibatkan semua tokoh masyarakat dan memaksa warga untuk ikut.", rationale: "Memaksa melanggar prinsip sukarela Gotong Roy Royong.", isCorrect: false },
                        { text: "Membersihkan area tersebut sambil mengadakan workshop pengolahan limbah menjadi ecobrick atau kompos untuk nilai ekonomi.", rationale: "Menggabungkan aksi fisik dengan edukasi dan nilai tambah (ekonomi) adalah inovasi.", isCorrect: true },
                        { text: "Mengevaluasi kegiatan setelah enam bulan berjalan.", rationale: "Evaluasi adalah bagian dari akuntabilitas, bukan inovasi metode.", isCorrect: false },
                        { text: "Hanya fokus pada penggalangan dana untuk membeli alat kebersihan yang mahal.", rationale: "Fokus berlebihan pada dana, bukan pada solusi akar masalah.", isCorrect: false },
                    ]
                },
                {
                    questionNumber: 23,
                    category: "Penerapan",
                    question: "Dalam proyek pembangunan taman kota, Anda mendelegasikan tugas logistik (menyediakan air minum dan makanan ringan) kepada Sari. Tindakan ini merupakan implementasi dari keterampilan kepemimpinan...",
                    hint: "Keterampilan apa yang melibatkan pembagian tugas dan tanggung jawab?",
                    imageUrl: "",
                    answerOptions: [
                        { text: "Motivasi", rationale: "Motivasi adalah membangkitkan semangat, bukan membagi tugas.", isCorrect: false },
                        { text: "Komunikasi Efektif", rationale: "Komunikasi adalah caranya, Delegasi adalah tujuannya.", isCorrect: false },
                        { text: "Delegasi Tugas", rationale: "Delegasi adalah membagikan tanggung jawab sesuai kemampuan untuk memastikan setiap orang merasa dihargai dan memiliki peran.", isCorrect: true },
                        { text: "Manajemen Konflik", rationale: "Ini tidak ada konflik yang dikelola.", isCorrect: false },
                        { text: "Akuntabilitas", rationale: "Akuntabilitas dilakukan setelah tugas selesai.", isCorrect: false },
                    ]
                },
                {
                    questionNumber: 24,
                    category: "Penerapan",
                    question: "Untuk mengatasi tantangan individualisme di lingkungan RT Anda, kegiatan Gotong Royong yang paling efektif dan berorientasi pada peningkatan interaksi sosial adalah...",
                    hint: "Pilih kegiatan yang membutuhkan koordinasi dan interaksi tatap muka yang tinggi.",
                    imageUrl: "",
                    answerOptions: [
                        { text: "Pengumpulan donasi online untuk warga miskin.", rationale: "Donasi online adalah Gotong Royong digital, interaksi sosialnya rendah.", isCorrect: false },
                        { text: "Pembersihan selokan yang membutuhkan koordinasi fisik dan pembagian kelompok kerja yang jelas.", rationale: "Aksi fisik yang membutuhkan kerja tim dan tatap muka adalah cara terbaik mengatasi individualisme.", isCorrect: true },
                        { text: "Rapat rutin RT untuk membahas masalah administrasi.", rationale: "Rapat administrasi kurang efektif untuk membangun ikatan sosial yang kuat.", isCorrect: false },
                        { text: "Lomba dekorasi rumah di mana setiap rumah bekerja sendiri-sendiri.", rationale: "Meskipun melibatkan lingkungan, ini tetap berfokus pada individu/rumah.", isCorrect: false },
                        { text: "Membuat grup *chat* WhatsApp untuk berbagi informasi.", rationale: "Ini adalah interaksi digital, bukan mengatasi individualisme secara fisik.", isCorrect: false },
                    ]
                },
                {
                    questionNumber: 25,
                    category: "Penerapan",
                    question: "Jika Anda merancang proyek untuk mendukung UMKM lokal (Ekonomi Kreatif), bentuk Gotong Royong yang paling relevan adalah...",
                    hint: "Fokus pada cara UMKM dapat bekerja sama untuk keuntungan kolektif.",
                    imageUrl: "",
                    answerOptions: [
                        { text: "Setiap UMKM bersaing untuk mendapatkan dana CSR dari perusahaan besar.", rationale: "Ini adalah persaingan, bukan Gotong Royong.", isCorrect: false },
                        { text: "Kerja sama antar UMKM untuk membuat *co-working space* bersama dan melakukan pemasaran produk secara kolektif.", rationale: "Kolaborasi dalam fasilitas dan pemasaran adalah kunci keberhasilan ekonomi kreatif berbasis komunitas.", isCorrect: true },
                        { text: "Setiap UMKM menyumbang dana untuk proyek pembangunan jalan desa.", rationale: "Ini Gotong Royong umum, bukan yang paling relevan untuk mendukung *Ekonomi Kreatif*.", isCorrect: false },
                        { text: "Mengadakan seminar tentang tips sukses menjadi *entrepreneur* mandiri.", rationale: "Seminar adalah edukasi individual, Gotong Royong adalah aksi kolektif.", isCorrect: false },
                        { text: "Mengundang investor dari luar negeri untuk mengambil alih manajemen UMKM.", rationale: "Ini menghilangkan aspek 'berbasis komunitas' dan 'Gotong Royong'.", isCorrect: false },
                    ]
                },
                {
                    questionNumber: 26,
                    category: "Penerapan",
                    question: "Salah satu anggota tim proyek Gotong Royong Anda merasa tersinggung karena komentarnya tidak didengar. Sebagai pemimpin, langkah pertama yang harus Anda ambil adalah...",
                    hint: "Fokus pada keterampilan 'Komunikasi' dan 'Manajemen Konflik' personal.",
                    imageUrl: "",
                    answerOptions: [
                        { text: "Mengabaikannya karena kepentingan proyek lebih besar dari perasaan individu.", rationale: "Mengabaikan akan memperburuk situasi dan merusak semangat tim.", isCorrect: false },
                        { text: "Meminta anggota tersebut untuk meninggalkan proyek jika tidak mau bekerja sama.", rationale: "Ini adalah solusi terakhir, bukan langkah pertama.", isCorrect: false },
                        { text: "Meminta maaf secara pribadi dan mendengarkan keluhannya untuk menerapkan 'Manajemen Konflik' dini.", rationale: "Langkah pertama adalah mendengarkan dan memvalidasi perasaan untuk mencegah konflik lebih lanjut.", isCorrect: true },
                        { text: "Mendelegasikannya tugas yang paling sulit sebagai hukuman.", rationale: "Hukuman bertentangan dengan prinsip motivasi sukarela Gotong Royong.", isCorrect: false },
                        { text: "Mengumumkan di depan umum bahwa komentar semua orang akan didengarkan.", rationale: "Ini perlu dilakukan, tetapi tindakan personal (meminta maaf) harus dilakukan terlebih dahulu.", isCorrect: false },
                    ]
                },
                {
                    questionNumber: 27,
                    category: "Penerapan",
                    question: "Sebuah tim Gotong Royong telah selesai membangun jembatan kecil. Tahap selanjutnya yang wajib dilakukan untuk menunjukkan 'Akuntabilitas' dan 'Pembelajaran' adalah...",
                    hint: "Apa output resmi dari tahap evaluasi pasca-proyek?",
                    imageUrl: "",
                    answerOptions: [
                        { text: "Langsung mencari proyek pembangunan lain yang lebih besar.", rationale: "Melewatkan tahap evaluasi dan akuntabilitas adalah praktik yang buruk.", isCorrect: false },
                        { text: "Mengadakan pesta perayaan besar untuk semua relawan dan masyarakat.", rationale: "Perayaan adalah apresiasi, bukan akuntabilitas.", isCorrect: false },
                        { text: "Mengumpulkan umpan balik (*feedback*) dan membuat laporan ringkas tentang proses kerja, biaya, dan hasil yang dicapai.", rationale: "Laporan dan umpan balik adalah inti dari akuntabilitas dan pembelajaran bagi proyek selanjutnya.", isCorrect: true },
                        { text: "Mengembalikan semua alat kerja yang dipinjam dari masyarakat.", rationale: "Ini adalah bagian dari logistik penutupan, bukan fokus utama akuntabilitas.", isCorrect: false },
                        { text: "Meminta bantuan pemerintah untuk merawat jembatan tersebut.", rationale: "Ini adalah tindak lanjut, bukan akuntabilitas atas proyek yang sudah selesai.", isCorrect: false },
                    ]
                },
                {
                    questionNumber: 28,
                    category: "Penerapan",
                    question: "Anda ingin menggalang dana untuk beasiswa anak tidak mampu. Pemanfaatan peluang Gotong Royong Digital yang paling tepat adalah...",
                    hint: "Fokus pada platform yang efisien untuk pengumpulan dana massal.",
                    imageUrl: "",
                    answerOptions: [
                        { text: "Membuat grup *chat* di Telegram untuk berkomunikasi dengan para donatur.", rationale: "Ini hanya alat komunikasi, bukan penggalangan dana efektif.", isCorrect: false },
                        { text: "Mengadakan penggalangan dana di *car free day* setiap akhir pekan.", rationale: "Ini adalah Gotong Royong fisik, bukan digital.", isCorrect: false },
                        { text: "Menggunakan platform *crowdfunding* resmi untuk menggalang dana dengan jangkauan nasional atau global.", rationale: "*Crowdfunding* adalah cara paling efektif memanfaatkan digitalisasi untuk pengumpulan dana massal.", isCorrect: true },
                        { text: "Membuat video dokumenter tentang anak-anak tersebut dan mengunggahnya di YouTube.", rationale: "Ini adalah media sosialisasi, bukan mekanisme penggalangan dananya.", isCorrect: false },
                        { text: "Menjual hasil kerajinan tangan untuk menambah dana beasiswa.", rationale: "Ini adalah UMKM, bukan fokus pada digitalisasi Gotong Royong.", isCorrect: false },
                    ]
                },
                {
                    questionNumber: 29,
                    category: "Penerapan",
                    question: "Dalam sesi Gotong Royong, dua kelompok relawan berdebat tentang cara terbaik menanam pohon (metode A vs. metode B). Sebagai pemimpin, cara terbaik untuk menerapkan 'Manajemen Konflik' adalah...",
                    hint: "Pikirkan tentang pendekatan yang paling adil dan rasional.",
                    imageUrl: "",
                    answerOptions: [
                        { text: "Mengambil keputusan sendiri dan mengabaikan kedua metode tersebut.", rationale: "Keputusan sepihak merusak rasa kepemilikan dan sukarela.", isCorrect: false },
                        { text: "Memecat kedua pemimpin kelompok karena dianggap mengganggu ketertiban.", rationale: "Ini terlalu ekstrem dan tidak mencerminkan resolusi konflik yang suportif.", isCorrect: false },
                        { text: "Menjelaskan tujuan akhir dan meminta kedua kelompok menguji metode mereka dalam skala kecil untuk melihat mana yang paling efisien.", rationale: "Ini adalah manajemen konflik berbasis data dan tujuan, fokus pada solusi kolektif.", isCorrect: true },
                        { text: "Memberi tahu kedua kelompok bahwa metode B adalah metode yang benar dan harus diikuti.", rationale: "Ini bersifat otoriter, bukan kolaboratif, dan mungkin salah.", isCorrect: false },
                        { text: "Menunda kegiatan sampai kedua kelompok mencapai kesepakatan sendiri.", rationale: "Penundaan proyek tidak menyelesaikan konflik dan menghambat kemajuan.", isCorrect: false },
                    ]
                },
                {
                    questionNumber: 30,
                    category: "Penerapan",
                    question: "Proposal kegiatan Anda bertujuan 'Meningkatkan kesadaran lingkungan siswa kelas XII sebesar 30% dalam waktu tiga bulan.' Kriteria *SMART* yang paling terpenuhi pada tujuan ini adalah...",
                    hint: "Fokus pada angka persentase dan batasan waktu.",
                    imageUrl: "",
                    answerOptions: [
                        { text: "Achievable (A) dan Relevan (R)", rationale: "Meskipun mungkin relevan dan dapat dicapai, kriteria yang paling menonjol adalah pengukuran dan waktu.", isCorrect: false },
                        { text: "Measurable (M) dan Time-bound (T)", rationale: "Angka '30%' membuat tujuan Terukur (M), dan 'tiga bulan' membuatnya Terikat Waktu (T).", isCorrect: true },
                        { text: "Specific (S) dan Achievable (A)", rationale: "Tujuan ini spesifik, namun M dan T adalah yang paling jelas ditunjukkan.", isCorrect: false },
                        { text: "Hanya Terikat Waktu (T) saja", rationale: "Tujuan ini juga terukur ('sebesar 30%') dan spesifik ('kesadaran lingkungan siswa kelas XII').", isCorrect: false },
                        { text: "Hanya Relevan (R) saja", rationale: "Relevansi adalah kriteria umum, tidak spesifik pada struktur kalimat tersebut.", isCorrect: false },
                    ]
                },
                {
                    questionNumber: 31,
                    category: "Penerapan",
                    question: "Untuk memastikan Gotong Royong berjalan efektif dan tidak ada yang merasa tidak adil, pemimpin harus menerapkan keterampilan 'Delegasi Tugas' dengan prinsip...",
                    hint: "Pikirkan tentang kesesuaian antara orang dan tugas.",
                    imageUrl: "",
                    answerOptions: [
                        { text: "Memastikan tugas yang paling berat selalu diberikan kepada relawan yang paling rajin.", rationale: "Ini akan menyebabkan kelelahan pada relawan yang rajin (burnout) dan ketidakadilan.", isCorrect: false },
                        { text: "Membagikan tugas tanpa memandang kemampuan, asalkan semua orang mendapatkan bagian.", rationale: "Delegasi harus didasarkan pada kemampuan agar tugas berhasil.", isCorrect: false },
                        { text: "Membagi tanggung jawab berdasarkan minat dan kemampuan individu, serta memberikan pelatihan jika diperlukan.", rationale: "Delegasi yang sukses memastikan tugas dilakukan dengan baik dan relawan merasa dihargai kemampuannya.", isCorrect: true },
                        { text: "Hanya mendelegasikan tugas kepada anggota tim inti, sedangkan masyarakat umum hanya disuruh membantu.", rationale: "Ini melanggar prinsip pemberdayaan masyarakat.", isCorrect: false },
                        { text: "Meminta relawan untuk memilih sendiri tugas mereka, tanpa intervensi pemimpin.", rationale: "Ini bisa menyebabkan tugas-tugas penting terabaikan.", isCorrect: false },
                    ]
                },
                {
                    questionNumber: 32,
                    category: "Penerapan",
                    question: "Anda ingin menginisiasi program Gotong Royong di sekolah. Sebelum membentuk tim inti, langkah penting yang harus Anda lakukan untuk 'Identifikasi Kebutuhan' adalah...",
                    hint: "Anda harus menentukan masalah apa yang paling mendesak dan relevan bagi lingkungan sekolah.",
                    imageUrl: "",
                    answerOptions: [
                        { text: "Langsung membuat proposal dengan anggaran yang besar.", rationale: "Anggaran dibuat setelah identifikasi kebutuhan dan tujuan.", isCorrect: false },
                        { text: "Menyelenggarakan acara sosialisasi untuk menarik perhatian siswa.", rationale: "Sosialisasi dilakukan setelah proyek dirancang.", isCorrect: false },
                        { text: "Melakukan survei, observasi, atau musyawarah kecil untuk menentukan masalah (sampah, fasilitas, literasi) yang paling mendesak di sekolah.", rationale: "Inisiasi harus dimulai dengan identifikasi masalah yang valid.", isCorrect: true },
                        { text: "Mencari *endorsement* dari kepala sekolah dan guru-guru.", rationale: "Dukungan didapatkan setelah inisiasi kebutuhan dasar.", isCorrect: false },
                        { text: "Membuat logo proyek yang menarik dan *catchy*.", rationale: "Logo adalah bagian dari branding, bukan identifikasi kebutuhan.", isCorrect: false },
                    ]
                },
                {
                    questionNumber: 33,
                    category: "Penerapan",
                    question: "Sebuah proyek Gotong Royong yang sukses dan berkesinambungan selalu melakukan 'Motivasi dan Apresiasi.' Bentuk apresiasi yang paling efektif dan sederhana pasca-kegiatan adalah...",
                    hint: "Pilih bentuk apresiasi yang bersifat personal dan mendalam, bukan hanya materi.",
                    imageUrl: "",
                    answerOptions: [
                        { text: "Memberikan uang tunai kepada semua relawan sesuai jumlah jam kerja mereka.", rationale: "Ini mengubah Gotong Royong menjadi pekerjaan berbayar (transaksional).", isCorrect: false },
                        { text: "Mengadakan *gala dinner* mewah di hotel berbintang lima.", rationale: "Ini terlalu mahal dan boros. Apresiasi harus sederhana dan fokus.", isCorrect: false },
                        { text: "Mengirimkan ucapan terima kasih personal melalui surat/media sosial, dan mengakui kontribusi spesifik setiap orang dalam laporan.", rationale: "Pengakuan dan ucapan terima kasih personal adalah bentuk apresiasi non-materiil yang paling berharga.", isCorrect: true },
                        { text: "Mengumumkan bahwa semua relawan akan mendapatkan nilai A di mata pelajaran PPKn.", rationale: "Apresiasi harus datang dari tim proyek, bukan manipulasi nilai akademis.", isCorrect: false },
                        { text: "Langsung membubarkan tim tanpa ada acara penutupan.", rationale: "Ini adalah praktik buruk dan merusak semangat tim.", isCorrect: false },
                    ]
                },
                {
                    questionNumber: 34,
                    category: "Penerapan",
                    question: "Peluang Gotong Royong dalam 'Ketahanan Bencana' mencakup tahap tanggap darurat, rehabilitasi, dan rekonstruksi. Contoh aksi Gotong Royong pada tahap **rehabilitasi** adalah...",
                    hint: "Rehabilitasi berfokus pada pemulihan kondisi agar masyarakat dapat kembali normal.",
                    imageUrl: "",
                    answerOptions: [
                        { text: "Evakuasi korban dari lokasi bencana ke tempat yang aman.", rationale: "Ini adalah tahap Tanggap Darurat.", isCorrect: false },
                        { text: "Mendirikan rumah sakit darurat dan dapur umum segera setelah bencana terjadi.", rationale: "Ini adalah tahap Tanggap Darurat.", isCorrect: false },
                        { text: "Membantu perbaikan infrastruktur sekolah yang rusak agar kegiatan belajar mengajar dapat dilanjutkan.", rationale: "Membantu pemulihan fasilitas dan layanan publik adalah inti dari tahap Rehabilitasi.", isCorrect: true },
                        { text: "Membangun kembali seluruh rumah dan gedung secara permanen di lokasi baru.", rationale: "Ini adalah tahap Rekonstruksi.", isCorrect: false },
                        { text: "Menganalisis penyebab bencana dan membuat peta risiko.", rationale: "Ini adalah tahap Mitigasi (pencegahan), bukan rehabilitasi.", isCorrect: false },
                    ]
                },
                {
                    questionNumber: 35,
                    category: "Penerapan",
                    question: "Mengapa dalam fase 'Sosialisasi dan Mobilisasi' sebuah proyek Gotong Royong, penekanan pada *kesempatan untuk berkontribusi* lebih penting daripada *kewajiban untuk membantu*?",
                    hint: "Pikirkan tentang *prinsip dasar* Gotong Royong.",
                    imageUrl: "",
                    answerOptions: [
                        { text: "Karena Gotong Royong adalah prinsip sukarela, sehingga penekanan pada kewajiban akan terasa memaksa dan melanggar esensinya.", rationale: "Keterlibatan yang sukarela (kesempatan) menghasilkan komitmen yang lebih tulus daripada kewajiban yang dipaksakan.", isCorrect: true },
                        { text: "Karena masyarakat Indonesia tidak menyukai kata 'kewajiban'.", rationale: "Alasannya lebih pada filosofi Gotong Royong, bukan preferensi linguistik.", isCorrect: false },
                        { text: "Karena hanya relawan yang profesional yang boleh merasa berkewajiban.", rationale: "Semua anggota masyarakat memiliki tanggung jawab moral, tetapi partisipasi tetap sukarela.", isCorrect: false },
                        { text: "Karena 'kewajiban' hanya berlaku untuk proyek yang didanai pemerintah.", rationale: "Kata 'kewajiban' tidak tergantung pada sumber dana.", isCorrect: false },
                        { text: "Karena masyarakat yang sudah terbiasa dengan individualisme akan menolak kewajiban sosial.", rationale: "Meskipun individualisme adalah tantangan, alasan utamanya tetap prinsip sukarela Gotong Royong.", isCorrect: false },
                    ]
                },

                // Kategori Identifikasi Cerita (36-40) - Case Study
                {
                    questionNumber: 36,
                    category: "Identifikasi Cerita",
                    question: "Studi Kasus: Pak Budi, Ketua RT 05, kesulitan mengajak warganya Gotong Royong membersihkan saluran air. Sebagian besar warga, terutama generasi muda, sibuk bekerja dan menghabiskan waktu luang di media sosial, merasa membersihkan saluran adalah tugas petugas kebersihan. Pertanyaan: Tantangan utama Gotong Royong yang dihadapi Pak Budi adalah...",
                    hint: "Fokus pada pola pikir *individual* dan *apatis* terhadap tugas komunal.",
                    imageUrl: "",
                    answerOptions: [
                        { text: "Polarisasi Politik/Sosial", rationale: "Tidak ada indikasi perpecahan politik; masalahnya adalah apatis sosial.", isCorrect: false },
                        { text: "Erosi Nilai oleh Globalisasi", rationale: "Ini terlalu umum. Tantangan yang lebih spesifik adalah individualisme dan digitalisasi yang mengarah pada apatis.", isCorrect: false },
                        { text: "Gaya Hidup Digital (Tidak Produktif) dan Individualisme", rationale: "Siswa sibuk bekerja (Individualisme) dan menghabiskan waktu di media sosial (Gaya Hidup Digital) yang membuat mereka menolak tugas komunal.", isCorrect: true },
                        { text: "Kurangnya Dana Anggaran", rationale: "Masalahnya adalah partisipasi, bukan dana.", isCorrect: false },
                        { text: "Krisis Ketahanan Bencana", rationale: "Masalahnya adalah kebersihan rutin, bukan kondisi bencana.", isCorrect: false },
                    ]
                },
                {
                    questionNumber: 37,
                    category: "Identifikasi Cerita",
                    question: "Studi Kasus: Sebuah kelompok mahasiswa merancang proyek 'Buku Bergerak' di mana mereka mengumpulkan donasi buku, mendirikan perpustakaan mini di lima lokasi berbeda, dan mengadakan sesi membaca mingguan. Mereka menggunakan aplikasi untuk melacak donasi dan jadwal relawan. Pertanyaan: Prinsip peluang Gotong Royong mana yang paling dominan diterapkan dalam proyek 'Buku Bergerak' ini?",
                    hint: "Proyek ini menggunakan teknologi untuk mengatur aksi sosial.",
                    imageUrl: "",
                    answerOptions: [
                        { text: "Ekonomi Kreatif Berbasis Komunitas", rationale: "Meskipun ada kegiatan, fokus utamanya adalah literasi dan kolaborasi (non-ekonomi).", isCorrect: false },
                        { text: "Ketahanan Bencana (Resiliensi)", rationale: "Proyek ini tidak terkait dengan penanggulangan bencana.", isCorrect: false },
                        { text: "Digitalisasi Kolaborasi", rationale: "Menggunakan aplikasi untuk melacak donasi dan jadwal relawan adalah pemanfaatan teknologi untuk memfasilitasi aksi kolektif.", isCorrect: true },
                        { text: "Penguatan Demokrasi Lokal", rationale: "Fokusnya adalah pendidikan/literasi, bukan mekanisme politik.", isCorrect: false },
                        { text: "Peningkatan Sarana Fisik Tradisional", rationale: "Meskipun mendirikan perpustakaan mini, penggunaan aplikasi membuatnya lebih dari sekadar tradisional.", isCorrect: false },
                    ]
                },
                {
                    questionNumber: 38,
                    category: "Identifikasi Cerita",
                    question: "Studi Kasus: Tim Gotong Royong Lingkungan telah selesai menanam 500 bibit pohon di lahan kritis. Setelah kegiatan, ketua tim mengadakan pertemuan singkat, mencatat berapa banyak bibit yang ditanam, berapa banyak relawan yang datang, dan menanyakan saran perbaikan untuk acara berikutnya. Pertanyaan: Tindakan ketua tim tersebut paling tepat mencerminkan tahapan kepemimpinan Gotong Royong yang disebut...",
                    hint: "Ini adalah tindakan pasca-proyek yang berfokus pada pertanggungjawaban dan evaluasi.",
                    imageUrl: "",
                    answerOptions: [
                        { text: "Delegasi Tugas", rationale: "Delegasi terjadi sebelum dan selama pelaksanaan.", isCorrect: false },
                        { text: "Motivasi dan Apresiasi", rationale: "Meskipun mengapresiasi, fokusnya pada pencatatan dan saran perbaikan (evaluasi).", isCorrect: false },
                        { text: "Sosialisasi dan Mobilisasi", rationale: "Ini adalah tahapan pra-pelaksanaan.", isCorrect: false },
                        { text: "Akuntabilitas & Evaluasi", rationale: "Mencatat hasil, jumlah relawan, dan mengumpulkan saran perbaikan adalah bagian dari Akuntabilitas dan Evaluasi pasca-proyek.", isCorrect: true },
                        { text: "Inisiasi dan Perancangan", rationale: "Tahap ini terjadi sebelum proyek dimulai.", isCorrect: false },
                    ]
                },
                {
                    questionNumber: 39,
                    category: "Identifikasi Cerita",
                    question: "Studi Kasus: Proposal kegiatan 'Bank Sampah Digital' mencantumkan tujuan: 'Meningkatkan kesadaran masyarakat tentang daur ulang.' Pendanaan utama berasal dari penjualan sampah kering. Pertanyaan: Berdasarkan kriteria proposal yang inovatif, langkah perbaikan paling krusial untuk rancangan kegiatan ini adalah...",
                    hint: "Fokus pada 'inovasi' dan 'sistematis' dalam metode kegiatan.",
                    imageUrl: "",
                    answerOptions: [
                        { text: "Menghapus kata 'Digital' karena lebih baik fokus pada Bank Sampah fisik.", rationale: "Menghapus digitalisasi menghilangkan aspek inovatif.", isCorrect: false },
                        { text: "Mengubah tujuan menjadi 'Mencapai target pendapatan Rp 10.000.000 dari penjualan sampah'.", rationale: "Tujuan finansial menggeser fokus dari masalah sosial/lingkungan.", isCorrect: false },
                        { text: "Mencantumkan rincian metode bagaimana teknologi digital digunakan untuk edukasi, transaksi, dan pelacakan sampah warga.", rationale: "Metode yang jelas dan inovatif adalah kunci untuk proposal sistematis.", isCorrect: true },
                        { text: "Mengganti nama proyek menjadi 'Gotong Royong Sampah'.", rationale: "Perubahan nama tidak memperbaiki substansi rancangan kegiatan.", isCorrect: false },
                        { text: "Menambahkan anggaran untuk membeli seragam baru bagi semua relawan.", rationale: "Ini adalah detail anggaran, bukan perbaikan krusial pada metode.", isCorrect: false },
                    ]
                },
                {
                    questionNumber: 40,
                    category: "Identifikasi Cerita",
                    question: "Studi Kasus: Warga Desa Sukamaju mengadakan musyawarah untuk menentukan prioritas pembangunan. Terdapat dua usulan kuat: membangun fasilitas olahraga (diinginkan pemuda) atau memperbaiki jalan desa (diinginkan lansia dan petani). Setelah diskusi yang panjang, keputusan diambil untuk memperbaiki jalan terlebih dahulu, didukung oleh semua pihak. Pertanyaan: Prinsip kepemimpinan Gotong Royong mana yang berhasil mengatasi konflik kepentingan dalam studi kasus ini?",
                    hint: "Meskipun ada perdebatan, hasilnya adalah persetujuan kolektif.",
                    imageUrl: "",
                    answerOptions: [
                        { text: "Delegasi Tugas", rationale: "Tidak ada pembagian tugas yang terlibat, hanya resolusi konflik.", isCorrect: false },
                        { text: "Manajemen Konflik dan Konsensus", rationale: "Konflik kepentingan berhasil dikelola melalui musyawarah hingga mencapai kesepakatan yang didukung semua pihak (konsensus).", isCorrect: true },
                        { text: "Komunikasi Efektif", rationale: "Meskipun menggunakan komunikasi, fokusnya adalah pada penyelesaian masalah (konflik).", isCorrect: false },
                        { text: "Akuntabilitas", rationale: "Akuntabilitas adalah tahap pasca-kegiatan.", isCorrect: false },
                        { text: "Individualisme", rationale: "Hasilnya adalah kepentingan kolektif yang diprioritaskan, berlawanan dengan individualisme.", isCorrect: false },
                    ]
                },
            ]
        };

        let currentQuestionIndex = 0;
        let score = 0;
        let isAnswered = false;
        let studentName = '';
        let studentClass = '';

        // --- UTILITY FUNCTIONS ---
        const getElement = (id) => document.getElementById(id);

        const renderIdentityPage = () => {
            const app = getElement('app');
            app.innerHTML = `
                <div class="max-w-md mx-auto p-8 bg-white rounded-xl shadow-2xl mt-12">
                    <h1 class="text-3xl font-bold text-center text-blue-700 mb-4">Selamat Datang di Kuis Gotong Royong</h1>
                    <p class="text-center text-gray-600 mb-6">Masukkan identitas Anda untuk memulai kuis 40 soal.</p>

                    <div class="mb-4">
                        <label for="name" class="block text-gray-700 font-semibold mb-2">Nama Lengkap</label>
                        <input type="text" id="name" placeholder="Nama Anda" class="w-full px-4 py-2 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-500" required>
                    </div>
                    <div class="mb-6">
                        <label for="class" class="block text-gray-700 font-semibold mb-2">Kelas (Contoh: XII IPA 1)</label>
                        <input type="text" id="class" placeholder="Kelas Anda" class="w-full px-4 py-2 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-500" required>
                    </div>

                    <button onclick="startQuiz()" class="w-full bg-blue-600 text-white py-3 rounded-xl font-bold hover:bg-blue-700 transition duration-300 shadow-md">
                        Mulai Kuis
                    </button>
                </div>
            `;
        };

        const startQuiz = () => {
            studentName = getElement('name').value.trim();
            studentClass = getElement('class').value.trim();

            if (!studentName || !studentClass) {
                alert('Nama dan Kelas wajib diisi untuk memulai kuis.');
                return;
            }

            currentQuestionIndex = 0;
            score = 0;
            renderQuizPage();
        };

        const renderQuizPage = () => {
            if (currentQuestionIndex >= quizData.questions.length) {
                renderScorePage();
                return;
            }

            const app = getElement('app');
            const q = quizData.questions[currentQuestionIndex];
            isAnswered = false;

            // Generate answer options buttons
            const optionsHTML = q.answerOptions.map((option, index) => `
                <button id="option-${index}"
                    class="option-button w-full text-left p-4 mb-3 border-2 border-gray-200 rounded-xl bg-white shadow-sm hover:border-blue-500 transition duration-200"
                    onclick="checkAnswer(${index}, ${q.questionNumber})">
                    <span class="font-bold text-blue-600">${String.fromCharCode(65 + index)}.</span> ${option.text}
                </button>
            `).join('');

            app.innerHTML = `
                <div class="container-quiz mx-auto p-4 md:p-8">
                    <div class="text-center mb-6">
                        <h1 class="text-2xl font-bold text-blue-700">Kuis Gotong Royong Kontemporer</h1>
                        <p class="text-gray-600">Soal ${currentQuestionIndex + 1} dari ${quizData.questions.length} | Kategori: ${q.category}</p>
                    </div>

                    <div class="question-card bg-white p-6 rounded-xl shadow-lg mb-6">
                        <p class="text-lg font-semibold text-gray-800 mb-4">${q.question}</p>
                        ${q.hint ? `<p class="text-sm text-gray-500 italic mb-4 p-2 bg-yellow-50 rounded-lg border border-yellow-200">Petunjuk: ${q.hint}</p>` : ''}
                        
                        <div id="options-container" class="space-y-3">
                            ${optionsHTML}
                        </div>

                        <div id="rationale-display" class="mt-4 p-4 rounded-lg hidden">
                            <!-- Rationale will be displayed here -->
                        </div>
                    </div>

                    <div class="flex justify-between items-center">
                        <p class="text-lg font-semibold text-gray-700">Skor Sementara: ${score}</p>
                        <button id="next-button" onclick="nextQuestion()" class="bg-green-600 text-white px-6 py-3 rounded-xl font-bold hover:bg-green-700 transition duration-300 disabled:opacity-50 disabled" disabled>
                            Soal Selanjutnya &rarr;
                        </button>
                    </div>
                </div>
            `;
        };

        const checkAnswer = (selectedIndex) => {
            if (isAnswered) return;
            isAnswered = true;

            const q = quizData.questions[currentQuestionIndex];
            const optionsContainer = getElement('options-container');
            const rationaleDisplay = getElement('rationale-display');
            const nextButton = getElement('next-button');

            // Disable all buttons
            Array.from(optionsContainer.children).forEach(btn => btn.classList.add('disabled'));

            q.answerOptions.forEach((option, index) => {
                const button = getElement(`option-${index}`);
                const isSelected = index === selectedIndex;

                button.classList.remove('hover:border-blue-500');

                if (option.isCorrect) {
                    button.classList.add('correct-answer', 'border-green-400');
                    if (isSelected) {
                        score++;
                    }
                } else if (isSelected) {
                    button.classList.add('incorrect-answer', 'border-red-400');
                }
                
                if (isSelected) {
                    button.classList.add('selected-option');
                }
            });

            // Display Rationale
            const selectedOption = q.answerOptions[selectedIndex];
            const isCorrect = selectedOption.isCorrect;
            const rationaleText = selectedOption.rationale;
            const rationaleClass = isCorrect ? 'bg-green-100 border border-green-400 text-green-800' : 'bg-red-100 border border-red-400 text-red-800';
            
            rationaleDisplay.innerHTML = `
                <p class="font-bold mb-1">${isCorrect ? 'Jawaban Benar! 🎉' : 'Jawaban Salah. 😔'}</p>
                <p class="text-sm">${rationaleText}</p>
            `;
            rationaleDisplay.className = `mt-4 p-4 rounded-lg ${rationaleClass}`;
            rationaleDisplay.style.display = 'block';

            // Enable next button
            nextButton.disabled = false;
            nextButton.classList.remove('disabled');
        };

        const nextQuestion = () => {
            currentQuestionIndex++;
            renderQuizPage();
        };

        const renderScorePage = () => {
            const totalQuestions = quizData.questions.length;
            const finalScore = (score / totalQuestions) * 100;
            const scoreMessage = finalScore >= 75 ? 'Hebat! Pemahaman Anda tentang Gotong Royong sangat baik.' : 'Perlu ditingkatkan. Mari kita pelajari kembali materi dan fokus pada analisis dan penerapan.';
            const app = getElement('app');

            app.innerHTML = `
                <div class="max-w-md mx-auto p-8 bg-white rounded-xl shadow-2xl mt-12 text-center">
                    <h1 class="text-4xl font-extrabold text-green-600 mb-4">Kuis Selesai!</h1>
                    <p class="text-xl font-semibold text-gray-700 mb-2">Terima kasih telah berpartisipasi, ${studentName}.</p>
                    <p class="text-lg text-gray-500 mb-6">Kelas: ${studentClass}</p>

                    <div class="bg-blue-50 p-6 rounded-xl mb-6 border-4 border-blue-400">
                        <p class="text-2xl font-semibold text-gray-700">Skor Akhir Anda:</p>
                        <p class="text-5xl font-bold mt-2 ${finalScore >= 75 ? 'text-green-600' : 'text-red-600'}">${score}/${totalQuestions}</p>
                        <p class="text-xl font-semibold mt-1">Nilai Persentase: ${finalScore.toFixed(2)}%</p>
                    </div>

                    <p class="text-md text-gray-700 italic mb-8">${scoreMessage}</p>

                    <button onclick="renderIdentityPage()" class="w-full bg-blue-600 text-white py-3 rounded-xl font-bold hover:bg-blue-700 transition duration-300 shadow-md">
                        Ulangi Kuis
                    </button>
                </div>
            `;
        };

        // Initialize the app
        window.onload = renderIdentityPage;
    </script>
</body>
</html>
