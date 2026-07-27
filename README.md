<!DOCTYPE html>
<html lang="id">
<head>
<body> 
<div id="google_translate_element"></div>  <-- TAROH DISINI

<script type="text/javascript">
function googleTranslateElementInit() {
  new google.translate.TranslateElement({pageLanguage: 'id'}, 'google_translate_element');
}
</script>

<script type="text/javascript" src="//translate.google.com/translate_a/element.js?cb=googleTranslateElementInit"></script>

<!-- Kode web lu yang lain taroh di bawah sini -->
<h1>Halo saya Mico</h1>

</body>
</html>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Mico Ardiansyah — Graphic Design</title>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Space+Grotesk:wght@400;500;600;700&family=Inter:wght@400;500;600&family=IBM+Plex+Mono:wght@400;500&display=swap" rel="stylesheet">
<style>
  /* ============ DESIGN TOKENS ============
     GANTI warna di sini kalau mau ubah tema.
     ink      = warna dasar background (orange terang, bukan orange pekat)
     paper    = warna teks utama (putih gading hangat)
     accent   = magenta terang (CTA, highlight, link aktif)
     accent-2 = mint (tag kategori, garis bawah, aksen sekunder)
  ============================================= */
  :root{
    --ink:rgb(245, 204, 67);
    --ink-soft:#fa8806;
    --ink-softer:#233D35;
    --paper:#ECEFE3;
    --paper-dim:#C9CFC0;
    --accent:#FF3D8A;
    --accent-2:#8CFFC0;
    --muted:#8FA396;
    --line: rgba(236,239,227,0.14);
    --line-strong: rgba(236,239,227,0.28);
    --font-display: 'Space Grotesk', sans-serif;
    --font-body: 'Inter', sans-serif;
    --font-mono: 'IBM Plex Mono', monospace;
  }

  *{ box-sizing:border-box; margin:0; padding:0; }
  html{ scroll-behavior:smooth; }
  body{
    background:var(--ink);
    color:var(--paper);
    font-family:var(--font-body);
    line-height:1.5;
    overflow-x:hidden;
    -webkit-font-smoothing:antialiased;
  }
  a{ color:inherit; text-decoration:none; }
  button{ font-family:inherit; cursor:pointer; border:none; background:none; color:inherit; }
  ::selection{ background:var(--accent); color:var(--ink); }

  .mono{ font-family:var(--font-mono); letter-spacing:0.02em; }
  .eyebrow{
    font-family:var(--font-mono);
    font-size:0.72rem;
    letter-spacing:0.16em;
    text-transform:uppercase;
    color:var(--muted);
    display:flex;
    align-items:center;
    gap:10px;
  }
  .eyebrow::before{
    content:'';
    width:7px; height:7px;
    background:var(--accent-2);
    display:inline-block;
    border-radius:1px;
  }

  /* ============ REGISTRATION MARK (signature element) ============ */
  .regmark{
    position:absolute;
    width:22px; height:22px;
    pointer-events:none;
    opacity:0.55;
  }
  .regmark::before, .regmark::after{
    content:'';
    position:absolute;
    background:var(--muted);
  }
  .regmark::before{ width:100%; height:1px; top:50%; left:0; }
  .regmark::after{ width:1px; height:100%; left:50%; top:0; }
  .regmark.tl{ top:14px; left:14px; }
  .regmark.tr{ top:14px; right:14px; }
  .regmark.bl{ bottom:14px; left:14px; }
  .regmark.br{ bottom:14px; right:14px; }

  /* ============ NAV ============ */
  header.site-nav{
    position:fixed; top:0; left:0; right:0;
    z-index:100;
    display:flex; align-items:center; justify-content:space-between;
    padding:22px clamp(20px,5vw,56px);
    background:linear-gradient(to bottom, var(--ink) 60%, transparent);
  }
  .logo{
    font-family:var(--font-display);
    font-weight:700;
    font-size:1.15rem;
    letter-spacing:-0.01em;
    display:flex; align-items:center; gap:10px;
  }
  .logo .dot{ width:8px; height:8px; background:var(--accent); border-radius:50%; display:inline-block; }
  nav.pages{
    display:flex; align-items:center; gap:6px;
    background:var(--ink-soft);
    border:1px solid var(--line);
    border-radius:100px;
    padding:5px;
  }
  nav.pages button{
    font-family:var(--font-mono);
    font-size:0.75rem;
    letter-spacing:0.08em;
    text-transform:uppercase;
    padding:9px 18px;
    border-radius:100px;
    color:var(--muted);
    transition:all .25s ease;
  }
  nav.pages button.active{
    background:var(--paper);
    color:var(--ink);
  }
  nav.pages button:hover:not(.active){ color:var(--paper); }
  .page-index{
    font-family:var(--font-mono);
    font-size:0.75rem;
    color:var(--muted);
    display:none;
  }
  @media(min-width:760px){ .page-index{ display:block; } }

  main{ min-height:100vh; }
  .page{ display:none; animation:fadeIn .5s ease; }
  .page.active{ display:block; }
  @keyframes fadeIn{ from{ opacity:0; transform:translateY(8px); } to{ opacity:1; transform:translateY(0); } }
  @media (prefers-reduced-motion: reduce){
    .page{ animation:none; }
    html{ scroll-behavior:auto; }
  }

  .wrap{ max-width:1240px; margin:0 auto; padding:0 clamp(20px,5vw,56px); }

  /* ============ ABOUT PAGE ============ */
  .about-hero{
    position:relative;
    padding:170px 0 90px;
    border-bottom:1px solid var(--line);
    overflow:hidden;
  }
  .about-hero .bg-mono{
    position:absolute;
    top:-40px; right:-20px;
    font-family:var(--font-display);
    font-weight:700;
    font-size:min(38vw,420px);
    color:var(--ink-soft);
    z-index:0;
    line-height:0.8;
    pointer-events:none;
    user-select:none;
  }
  .about-hero-inner{ position:relative; z-index:1; max-width:760px; }
  h1.display{
    font-family:var(--font-display);
    font-weight:700;
    font-size:clamp(2.6rem, 6.4vw, 5rem);
    line-height:1.02;
    letter-spacing:-0.02em;
    margin:18px 0 24px;
  }
  h1.display em{
    font-style:normal;
    color:var(--accent-2);
  }
  .lede{
    font-size:1.08rem;
    color:var(--paper-dim);
    max-width:560px;
    margin-bottom:36px;
  }
  .hero-cta{ display:flex; gap:14px; flex-wrap:wrap; }
  .btn{
    font-family:var(--font-mono);
    font-size:0.8rem;
    letter-spacing:0.06em;
    text-transform:uppercase;
    padding:14px 26px;
    border-radius:4px;
    display:inline-flex; align-items:center; gap:8px;
    transition:all .2s ease;
  }
  .btn-primary{ background:var(--accent); color:var(--ink); }
  .btn-primary:hover{ background:var(--accent-2); transform:translateY(-2px); }
  .btn-ghost{ border:1px solid var(--line-strong); color:var(--paper); }
  .btn-ghost:hover{ border-color:var(--accent-2); color:var(--accent-2); }

  .about-grid{
    padding:80px 0;
    display:grid;
    grid-template-columns:1fr;
    gap:60px;
    border-bottom:1px solid var(--line);
  }
  @media(min-width:900px){ .about-grid{ grid-template-columns: 1.1fr 0.9fr; gap:80px; } }
  .about-grid p{ color:var(--paper-dim); margin-bottom:16px; max-width:520px; }
  .about-grid p:last-of-type{ margin-bottom:0; }

  .fact-list{ border-top:1px solid var(--line); }
  .fact-row{
    display:flex; justify-content:space-between; align-items:baseline;
    padding:16px 0;
    border-bottom:1px solid var(--line);
    gap:20px;
  }
  .fact-row .k{ font-family:var(--font-mono); font-size:0.75rem; color:var(--muted); text-transform:uppercase; letter-spacing:0.08em; }
  .fact-row .v{ font-family:var(--font-display); font-weight:500; text-align:right; }

  .timeline{ padding:80px 0 110px; }
  .timeline h2{ font-family:var(--font-display); font-size:1.6rem; margin-bottom:36px; }
  .tl-item{
    display:grid;
    grid-template-columns:90px 1fr;
    gap:24px;
    padding:22px 0;
    border-top:1px solid var(--line);
    align-items:baseline;
  }
  .tl-item:last-child{ border-bottom:1px solid var(--line); }
  .tl-item .yr{ font-family:var(--font-mono); color:var(--accent-2); font-size:0.85rem; }
  .tl-item .role{ font-family:var(--font-display); font-weight:600; font-size:1.05rem; margin-bottom:4px; }
  .tl-item .co{ color:var(--muted); font-size:0.9rem; }

  /* ============ PORTFOLIO PAGE ============ */
  .work-header{ padding:150px 0 30px; }
  .work-header h1{
    font-family:var(--font-display); font-weight:700;
    font-size:clamp(2.2rem, 5vw, 3.4rem);
    letter-spacing:-0.02em;
    margin:16px 0 10px;
  }
  .work-header p{ color:var(--paper-dim); max-width:520px; }

  .filters{
    display:flex; gap:8px; flex-wrap:wrap;
    padding:26px 0 40px;
    position:sticky; top:78px; z-index:20;
    background:var(--ink);
  }
  .filters button{
    font-family:var(--font-mono); font-size:0.72rem; text-transform:uppercase; letter-spacing:0.06em;
    padding:9px 16px; border:1px solid var(--line-strong); border-radius:100px; color:var(--muted);
    transition:all .2s ease;
  }
  .filters button.active{ background:var(--paper); border-color:var(--paper); color:var(--ink); }
  .filters button:hover:not(.active){ border-color:var(--accent-2); color:var(--accent-2); }

  .grid{
    display:grid;
    grid-template-columns:repeat(2,1fr);
    gap:2px;
    background:var(--line);
    border-top:1px solid var(--line);
    border-bottom:1px solid var(--line);
    margin-bottom:120px;
  }
  @media(min-width:640px){ .grid{ grid-template-columns:repeat(3,1fr); } }
  @media(min-width:1000px){ .grid{ grid-template-columns:repeat(4,1fr); } }

  .plate{
    position:relative;
    background:var(--ink);
    cursor:pointer;
    overflow:hidden;
    aspect-ratio:4/5;
    opacity:0;
    transform:translateY(14px);
    transition:opacity .5s ease, transform .5s ease;
  }
  .plate.in-view{ opacity:1; transform:translateY(0); }
  .plate.hidden-item{ display:none; }
  .plate img{
    width:100%; height:100%; object-fit:cover;
    filter:grayscale(45%) contrast(1.02);
    transition:filter .4s ease, transform .5s ease;
    display:block;
  }
  .plate:hover img{ filter:grayscale(0%); transform:scale(1.04); }
  .plate .p-info{
    position:absolute; left:0; right:0; bottom:0;
    padding:14px 16px;
    background:linear-gradient(to top, rgba(18,33,29,0.92), transparent);
    transform:translateY(6px);
    opacity:0.92;
  }
  .plate .p-num{ font-family:var(--font-mono); font-size:0.68rem; color:var(--accent-2); margin-bottom:4px; }
  .plate .p-title{ font-family:var(--font-display); font-weight:600; font-size:0.92rem; line-height:1.2; }
  .plate .p-cat{ font-family:var(--font-mono); font-size:0.65rem; color:var(--muted); text-transform:uppercase; margin-top:3px; }

  /* ============ LIGHTBOX ============ */
  .lightbox{
    position:fixed; inset:0; z-index:200;
    background:rgba(10,18,15,0.94);
    display:none;
    align-items:center; justify-content:center;
    padding:30px;
  }
  .lightbox.open{ display:flex; }
  .lb-box{
    max-width:920px; width:100%;
    background:var(--ink-soft);
    border:1px solid var(--line-strong);
    border-radius:6px;
    overflow:hidden;
    position:relative;
  }
  .lb-box img{ width:100%; display:block; max-height:56vh; object-fit:cover; }
  .lb-meta{ padding:26px 30px 30px; }
  .lb-meta .p-num{ font-family:var(--font-mono); font-size:0.75rem; color:var(--accent-2); margin-bottom:8px; }
  .lb-meta h3{ font-family:var(--font-display); font-size:1.5rem; margin-bottom:8px; }
  .lb-meta .p-cat{ font-family:var(--font-mono); font-size:0.7rem; text-transform:uppercase; color:var(--muted); margin-bottom:14px; }
  .lb-meta p{ color:var(--paper-dim); font-size:0.92rem; max-width:600px; }
  .lb-close{
    position:absolute; top:16px; right:16px;
    width:38px; height:38px; border-radius:50%;
    background:var(--ink); border:1px solid var(--line-strong);
    display:flex; align-items:center; justify-content:center;
    font-size:1.1rem; z-index:2;
  }
  .lb-close:hover{ background:var(--accent); color:var(--ink); border-color:var(--accent); }

  /* ============ CONTACT PAGE ============ */
  .contact-wrap{
    padding:160px 0 120px;
    display:grid; grid-template-columns:1fr;
    gap:60px;
  }
  @media(min-width:900px){ .contact-wrap{ grid-template-columns:0.9fr 1.1fr; gap:90px; } }
  .contact-info h1{
    font-family:var(--font-display); font-weight:700;
    font-size:clamp(2.2rem,5vw,3.2rem);
    letter-spacing:-0.02em; margin:16px 0 20px;
  }
  .contact-info p{ color:var(--paper-dim); max-width:420px; margin-bottom:36px; }
  .contact-channel{
    display:flex; flex-direction:column; gap:18px;
    border-top:1px solid var(--line);
    padding-top:24px;
  }
  .contact-channel a, .contact-channel span{
    display:flex; justify-content:space-between; align-items:center;
    font-family:var(--font-mono); font-size:0.85rem;
    padding:12px 0; border-bottom:1px solid var(--line);
  }
  .contact-channel a:hover{ color:var(--accent-2); }
  .contact-channel .k{ color:var(--muted); }

  form.contact-form{ position:relative; }
  .field{ margin-bottom:22px; }
  .field label{
    display:block; font-family:var(--font-mono); font-size:0.72rem;
    text-transform:uppercase; letter-spacing:0.08em; color:var(--muted); margin-bottom:8px;
  }
  .field input, .field textarea{
    width:100%;
    background:var(--ink-soft);
    border:1px solid var(--line-strong);
    color:var(--paper);
    font-family:var(--font-body);
    font-size:0.98rem;
    padding:14px 16px;
    border-radius:4px;
    transition:border-color .2s ease;
  }
  .field input:focus, .field textarea:focus{
    outline:none; border-color:var(--accent-2);
  }
  .field textarea{ min-height:130px; resize:vertical; }
  .field.error input, .field.error textarea{ border-color:var(--accent); }
  .field .err-msg{ font-family:var(--font-mono); font-size:0.72rem; color:var(--accent); margin-top:6px; display:none; }
  .field.error .err-msg{ display:block; }

  .submit-row{ display:flex; align-items:center; gap:18px; flex-wrap:wrap; margin-top:8px; }
  .form-note{
    font-family:var(--font-mono); font-size:0.78rem; color:var(--accent-2);
    padding:14px 0; display:none;
  }
  .form-note.show{ display:block; }

  footer.site-footer{
    border-top:1px solid var(--line);
    padding:26px clamp(20px,5vw,56px);
    display:flex; justify-content:space-between; align-items:center;
    font-family:var(--font-mono); font-size:0.72rem; color:var(--muted);
    flex-wrap:wrap; gap:10px;
  }

  a[href]:focus-visible, button:focus-visible{
    outline:2px solid var(--accent-2); outline-offset:2px;
  }
</style>
</head>
<body>

<header class="site-nav">
  <div class="logo"><span class="dot"></span><span id="cfgName">RAKA PRATAMA</span></div>
  <nav class="pages">
    <button data-page="about" class="active">About</button>
    <button data-page="work">Portfolio</button>
    <button data-page="contact">Kontak</button>
  </nav>
  <div class="page-index mono" id="pageIndex">01 / 03</div>
</header>

<main>

  <!-- ============ PAGE 1 — ABOUT ============ -->
  <section class="page active" id="page-about">
    <div class="about-hero">
      <div class="bg-mono">RP</div>
      <div class="wrap about-hero-inner">
        <div class="eyebrow" id="cfgRole">Visual Designer — Berbasis di Bali</div>
        <h1 class="display"><span id="cfgHeroBefore">Merancang identitas visual yang</span> <em id="cfgHeroEm">diingat</em><span id="cfgHeroAfter">, bukan sekadar dilihat.</span></h1>
        <p class="lede" id="cfgLede">Saya membantu brand dan studio menerjemahkan ide menjadi sistem visual yang jelas — mulai dari identitas, desain digital, hingga materi cetak. 8 tahun mengerjakan proyek untuk klien lokal maupun internasional.</p>
        <div class="hero-cta">
          <button class="btn btn-primary" onclick="showPage('work')">Lihat Portfolio →</button>
          <button class="btn btn-ghost" onclick="showPage('contact')">Hubungi Saya</button>
        </div>
      </div>
    </div>

    <div class="wrap about-grid">
      <div>
        <div class="eyebrow" style="margin-bottom:18px;">Tentang</div>
        <div id="cfgBio"></div>
      </div>
      <div class="fact-list" id="cfgFacts"></div>
    </div>

    <div class="wrap timeline">
      <h2>Perjalanan</h2>
      <div id="cfgTimeline"></div>
    </div>
  </section>

  <!-- ============ PAGE 2 — PORTFOLIO ============ -->
  <section class="page" id="page-work">
    <div class="wrap work-header">
      <div class="eyebrow" id="cfgWorkEyebrow">36 Karya Terpilih</div>
      <h1 id="cfgWorkTitle">Portfolio Karya</h1>
      <p id="cfgWorkDesc">Kumpulan proyek brand identity, desain digital, editorial, packaging, dan ilustrasi dari beberapa tahun terakhir. Klik tiap karya untuk melihat detail.</p>
    </div>

    <div class="wrap">
      <div class="filters" id="filters">
        <button data-filter="all" class="active">Semua (36)</button>
        <button data-filter="branding">Branding</button>
        <button data-filter="digital">Digital</button>
        <button data-filter="editorial">Editorial</button>
        <button data-filter="packaging">Packaging</button>
        <button data-filter="illustration">Ilustrasi</button>
      </div>
    </div>

    <div class="wrap">
      <div class="grid" id="grid"></div>
    </div>
  </section>

  <!-- ============ PAGE 3 — CONTACT ============ -->
  <section class="page" id="page-contact">
    <div class="wrap contact-wrap">
      <div class="contact-info">
        <div class="eyebrow">Kontak</div>
        <h1 id="cfgContactTitle">Punya proyek? Mari ngobrol.</h1>
        <p id="cfgContactDesc">Isi form di samping atau kirim langsung ke email saya. Biasanya saya balas dalam 1–2 hari kerja.</p>
        <div class="contact-channel">
          <a href="#" id="cfgEmailLink"><span class="k">Email</span><span id="cfgEmailText"></span></a>
          <a href="#" onclick="return false;"><span class="k">Instagram</span><span id="cfgInstagram"></span></a>
          <a href="#" onclick="return false;"><span class="k">Lokasi</span><span id="cfgLocation"></span></a>
        </div>
      </div>

      <form class="contact-form" id="contactForm" novalidate>
        <div class="field" id="field-name">
          <label for="f-name">Nama Lengkap</label>
          <input type="text" id="f-name" name="name" placeholder="Nama Anda" autocomplete="name">
          <div class="err-msg">Nama wajib diisi.</div>
        </div>
        <div class="field" id="field-email">
          <label for="f-email">Email</label>
          <input type="email" id="f-email" name="email" placeholder="nama@email.com" autocomplete="email">
          <div class="err-msg">Masukkan alamat email yang valid.</div>
        </div>
        <div class="field" id="field-message">
          <label for="f-message">Pesan</label>
          <textarea id="f-message" name="message" placeholder="Ceritakan sedikit tentang proyek Anda..."></textarea>
          <div class="err-msg">Pesan tidak boleh kosong.</div>
        </div>
        <div class="submit-row">
          <button type="submit" class="btn btn-primary">Kirim Pesan</button>
          <span class="mono" style="font-size:0.72rem; color:var(--muted);">Membuka aplikasi email Anda</span>
        </div>
        <div class="form-note" id="formNote">✓ Aplikasi email Anda akan terbuka dengan pesan terisi. Kalau tidak otomatis terbuka, kirim langsung ke email di atas.</div>
      </form>
    </div>
  </section>

</main>

<footer class="site-footer">
  <span id="cfgFooter">© 2026 Raka Pratama — Visual Designer</span>
  <span>Dibuat dengan hairline &amp; tanda registrasi.</span>
</footer>

<!-- ============ LIGHTBOX ============ -->
<div class="lightbox" id="lightbox">
  <div class="lb-box">
    <button class="lb-close" id="lbClose" aria-label="Tutup">✕</button>
    <img id="lbImg" src="" alt="">
    <div class="lb-meta">
      <div class="p-num mono" id="lbNum"></div>
      <h3 id="lbTitle"></h3>
      <div class="p-cat mono" id="lbCat"></div>
      <p id="lbDesc"></p>
    </div>
  </div>
</div>

<script>
/* =========================================================================
   ⭐ EDIT SEMUA ISI WEBSITE DI SINI ⭐
   Ini SATU-SATUNYA tempat yang perlu Anda ubah untuk custom teks.
   Ganti nilai di dalam tanda kutip " ... ", jangan ubah nama key di kirinya.
   Setelah edit, simpan file & buka ulang di browser untuk lihat hasilnya.
   ========================================================================= */
  const CONFIG = {
    name: "RAKA PRATAMA",                 // nama yang muncul di navigasi & footer
    role: "Visual Designer — Berbasis di Bali", // sub-judul kecil di halaman About

    // Judul besar halaman About — dipecah 3 bagian karena kata tengah diberi warna aksen
    heroBefore: "Merancang identitas visual yang",
    heroEm: "diingat",                    // kata ini akan tampil berwarna mint
    heroAfter: ", bukan sekadar dilihat.",
    heroLede: "Saya membantu brand dan studio menerjemahkan ide menjadi sistem visual yang jelas — mulai dari identitas, desain digital, hingga materi cetak. 8 tahun mengerjakan proyek untuk klien lokal maupun internasional.",

    // Paragraf bio — tambah/hapus baris sesuka Anda
    bio: [
      "Saya desainer visual dengan fokus pada brand identity, desain editorial, dan antarmuka digital. Pendekatan saya dimulai dari riset kecil-kecilan tentang audiens dan konteks, baru kemudian masuk ke eksplorasi bentuk dan warna.",
      "Sebelum bekerja lepas, saya menghabiskan beberapa tahun di studio desain menangani proyek rebranding untuk klien F&B, media, dan teknologi. Sekarang saya menerima proyek secara selektif — biasanya 3–4 klien aktif dalam satu waktu.",
      "Di luar kerja klien, saya senang bereksperimen dengan tipografi cetak dan risograph."
    ],

    // Daftar fakta singkat di halaman About (kolom kanan)
    facts: [
      { k:"Lokasi", v:"Denpasar, Bali" },
      { k:"Fokus", v:"Brand · Editorial · Digital" },
      { k:"Pengalaman", v:"8 tahun" },
      { k:"Tools", v:"Figma, Illustrator, InDesign" },
      { k:"Ketersediaan", v:"Terbuka — Q4 2026" }
    ],

    // Riwayat karier — tambah/hapus objek untuk menambah/mengurangi baris
    timeline: [
      { yr:"2023—Kini", role:"Independent Designer", co:"Klien lepas — brand & produk digital" },
      { yr:"2020—2023", role:"Senior Visual Designer", co:"Studio Ruang, Jakarta" },
      { yr:"2018—2020", role:"Graphic Designer", co:"Lentera Kreatif" },
      { yr:"2016—2018", role:"Junior Designer", co:"Studio Nirmana" }
    ],

    // Halaman Portfolio
    workEyebrow: "36 Karya Terpilih",
    workTitle: "Portfolio Karya",
    workDesc: "Kumpulan proyek brand identity, desain digital, editorial, packaging, dan ilustrasi dari beberapa tahun terakhir. Klik tiap karya untuk melihat detail.",

    // Halaman Kontak
    contactTitle: "Punya proyek? Mari ngobrol.",
    contactDesc: "Isi form di samping atau kirim langsung ke email saya. Biasanya saya balas dalam 1–2 hari kerja.",
    email: "halo@rakapratama.design",     // dipakai juga untuk tombol kirim form
    instagram: "@rakapratama.design",
    location: "Denpasar, Bali",

    footer: "© 2026 Raka Pratama — Visual Designer"
  };

  function renderConfig(){
    document.getElementById('cfgName').textContent = CONFIG.name;
    document.getElementById('cfgRole').textContent = CONFIG.role;
    document.getElementById('cfgHeroBefore').textContent = CONFIG.heroBefore;
    document.getElementById('cfgHeroEm').textContent = CONFIG.heroEm;
    document.getElementById('cfgHeroAfter').textContent = CONFIG.heroAfter;
    document.getElementById('cfgLede').textContent = CONFIG.heroLede;

    document.getElementById('cfgBio').innerHTML = CONFIG.bio.map(p=>`<p>${p}</p>`).join('');

    document.getElementById('cfgFacts').innerHTML = CONFIG.facts.map(f=>
      `<div class="fact-row"><span class="k">${f.k}</span><span class="v">${f.v}</span></div>`
    ).join('');

    document.getElementById('cfgTimeline').innerHTML = CONFIG.timeline.map(t=>
      `<div class="tl-item"><div class="yr">${t.yr}</div><div><div class="role">${t.role}</div><div class="co">${t.co}</div></div></div>`
    ).join('');

    document.getElementById('cfgWorkEyebrow').textContent = CONFIG.workEyebrow;
    document.getElementById('cfgWorkTitle').textContent = CONFIG.workTitle;
    document.getElementById('cfgWorkDesc').textContent = CONFIG.workDesc;

    document.getElementById('cfgContactTitle').textContent = CONFIG.contactTitle;
    document.getElementById('cfgContactDesc').textContent = CONFIG.contactDesc;
    document.getElementById('cfgEmailLink').href = 'mailto:' + CONFIG.email;
    document.getElementById('cfgEmailText').textContent = CONFIG.email;
    document.getElementById('cfgInstagram').textContent = CONFIG.instagram;
    document.getElementById('cfgLocation').textContent = CONFIG.location;

    document.getElementById('cfgFooter').textContent = CONFIG.footer;
    document.title = CONFIG.name + " — " + CONFIG.role;
  }
  renderConfig();

/* =========================================================================
   ⭐ EDIT 36 KARYA PORTFOLIO DI SINI ⭐
   Setiap item butuh: title, category, img, desc.

   CARA PAKAI GAMBAR SENDIRI — pilih salah satu:
   1) GAMBAR LOKAL (paling mudah kalau upload ke hosting seperti Netlify/GitHub Pages):
      - Buat folder bernama "images" persis di sebelah file index.html ini.
      - Taruh 36 file gambar Anda di situ, misal: images/kopi-kita.jpg
      - Ganti field img: "images/kopi-kita.jpg"
   2) GAMBAR DARI URL (kalau gambar sudah di-upload ke internet, misal Imgur/Google Drive share-link/CDN):
      - Ganti field img: "https://link-gambar-anda.com/nama-file.jpg"

   category harus salah satu dari: branding | digital | editorial | packaging | illustration
   (dipakai untuk tombol filter di halaman Portfolio)
   ========================================================================= */
  const categories = ['branding','digital','editorial','packaging','illustration'];
  const titles = [
    'Kopi Kita — Brand Identity','Nusantara Records — Album Art','Lentera Journal — Editorial Layout',
    'Ruang Studio — Website Redesign','Aether App — UI Kit','Tanah Air Coffee — Packaging',
    'Studio Nirmana — Logo System','Ombak Festival — Poster Series','Meja Kayu — Furniture Branding',
    'Warna Magazine — Cover Story','Cerita Kita — Book Cover','Biru Laut — Product Packaging',
    'Anargya Fashion — Lookbook','Kertas & Tinta — Stationery Set','Pixel House — App Icon Set',
    'Rumah Kopi — Cafe Identity','Suara Kota — Podcast Cover','Hutan Studio — Illustration Set',
    'Garuda Tech — Landing Page','Malam Jazz — Event Branding','Kain Nusantara — Textile Pattern',
    'Bumi Organik — Packaging Line','Jendela Kreatif — Editorial Spread','Pelangi Kids — Character Set',
    'Batu Karang — Hotel Branding','Sinar Pagi — Newsletter Design','Gerimis Studio — Dashboard UI',
    'Akar Kayu — Furniture Catalog','Tenun Baru — Fabric Illustration','Ruang Dingin — Cold Brew Packaging',
    'Kota Tua — Map Illustration','Studio Awan — Mobile App','Bahasa Rupa — Typeface Specimen',
    'Perahu Kertas — Children Book','Cahaya Senja — Photo Book','Jalan Pulang — Travel Zine'
  ];
  const projects = titles.map((t,i)=>({
    id:i+1,
    title:t,
    category:categories[i % categories.length],
    img:`https://picsum.photos/seed/rakadesign-${i+1}/700/860`,
    desc:'Studi kasus singkat proyek ini: eksplorasi konsep, sistem visual, dan aplikasinya lintas media. Ganti deskripsi ini dengan cerita proyek Anda yang sebenarnya.'
  }));

  const grid = document.getElementById('grid');
  grid.innerHTML = projects.map(p => `
    <div class="plate" data-category="${p.category}" data-id="${p.id}">
      <img src="${p.img}" alt="${p.title}" loading="lazy">
      <div class="p-info">
        <div class="p-num mono">PLATE ${String(p.id).padStart(2,'0')}</div>
        <div class="p-title">${p.title}</div>
        <div class="p-cat">${p.category}</div>
      </div>
    </div>
  `).join('');

  /* ---- Page navigation ---- */
  const pageOrder = ['about','work','contact'];
  function showPage(id){
    document.querySelectorAll('.page').forEach(p => p.classList.remove('active'));
    document.getElementById('page-'+id).classList.add('active');
    document.querySelectorAll('nav.pages button').forEach(b => b.classList.toggle('active', b.dataset.page===id));
    const idx = pageOrder.indexOf(id)+1;
    document.getElementById('pageIndex').textContent = '0'+idx+' / 03';
    window.scrollTo({top:0, behavior:'instant' in window ? 'instant':'auto'});
  }
  document.querySelectorAll('nav.pages button').forEach(btn=>{
    btn.addEventListener('click', ()=>showPage(btn.dataset.page));
  });

  /* ---- Filters ---- */
  document.getElementById('filters').addEventListener('click', e=>{
    const btn = e.target.closest('button');
    if(!btn) return;
    document.querySelectorAll('#filters button').forEach(b=>b.classList.remove('active'));
    btn.classList.add('active');
    const filter = btn.dataset.filter;
    document.querySelectorAll('.plate').forEach(pl=>{
      const match = filter==='all' || pl.dataset.category===filter;
      pl.classList.toggle('hidden-item', !match);
    });
  });

  /* ---- Reveal on scroll ---- */
  const io = new IntersectionObserver(entries=>{
    entries.forEach(en=>{ if(en.isIntersecting) en.target.classList.add('in-view'); });
  }, {threshold:0.1});
  document.querySelectorAll('.plate').forEach(pl=>io.observe(pl));

  /* ---- Lightbox ---- */
  const lightbox = document.getElementById('lightbox');
  grid.addEventListener('click', e=>{
    const plate = e.target.closest('.plate');
    if(!plate) return;
    const p = projects[+plate.dataset.id - 1];
    document.getElementById('lbImg').src = p.img;
    document.getElementById('lbImg').alt = p.title;
    document.getElementById('lbNum').textContent = 'PLATE ' + String(p.id).padStart(2,'0');
    document.getElementById('lbTitle').textContent = p.title;
    document.getElementById('lbCat').textContent = p.category;
    document.getElementById('lbDesc').textContent = p.desc;
    lightbox.classList.add('open');
  });
  document.getElementById('lbClose').addEventListener('click', ()=>lightbox.classList.remove('open'));
  lightbox.addEventListener('click', e=>{ if(e.target===lightbox) lightbox.classList.remove('open'); });
  document.addEventListener('keydown', e=>{ if(e.key==='Escape') lightbox.classList.remove('open'); });

  /* ---- Contact form ---- */
  const form = document.getElementById('contactForm');
  form.addEventListener('submit', e=>{
    e.preventDefault();
    const name = document.getElementById('f-name');
    const email = document.getElementById('f-email');
    const message = document.getElementById('f-message');
    let valid = true;

    toggleError('field-name', name.value.trim()==='');
    const emailOk = /^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(email.value.trim());
    toggleError('field-email', !emailOk);
    toggleError('field-message', message.value.trim()==='');

    if(name.value.trim()==='' || !emailOk || message.value.trim()===''){ valid = false; }
    if(!valid) return;

    // GANTI: hubungkan ke Formspree/EmailJS/backend Anda kalau mau kirim tanpa buka aplikasi email.
    const subject = encodeURIComponent('Proyek baru dari ' + name.value.trim());
    const body = encodeURIComponent(`Nama: ${name.value.trim()}\nEmail: ${email.value.trim()}\n\nPesan:\n${message.value.trim()}`);
    window.location.href = `mailto:${CONFIG.email}?subject=${subject}&body=${body}`;

    document.getElementById('formNote').classList.add('show');
    form.reset();
  });

  function toggleError(fieldId, isError){
    document.getElementById(fieldId).classList.toggle('error', isError);
  }
</script>
</body>
</html>
