import { useState, useEffect } from "react";

// ─── Prayer Time Calculator ───────────────────────────────────────────────────
function toRad(d) { return d * Math.PI / 180; }
function toDeg(r) { return r * 180 / Math.PI; }
function fixHour(a) { return a - 24 * Math.floor(a / 24); }
function fixAngle(a) { return a - 360 * Math.floor(a / 360); }

function calcPrayerTimes(year, month, day, lat, lng, timezone) {
  const JD = (() => {
    let y = year, m = month, d = day;
    if (m <= 2) { y--; m += 12; }
    const A = Math.floor(y / 100);
    const B = 2 - A + Math.floor(A / 4);
    return Math.floor(365.25 * (y + 4716)) + Math.floor(30.6001 * (m + 1)) + d + B - 1524.5;
  })();
  const D = JD - 2451545.0;
  const g = fixAngle(357.529 + 0.98560028 * D);
  const q = fixAngle(280.459 + 0.98564736 * D);
  const L = fixAngle(q + 1.915 * Math.sin(toRad(g)) + 0.020 * Math.sin(toRad(2 * g)));
  const e = 23.439 - 0.00000036 * D;
  const RA = toDeg(Math.atan2(Math.cos(toRad(e)) * Math.sin(toRad(L)), Math.cos(toRad(L)))) / 15;
  const EqT = q / 15 - fixHour(RA);
  const decl = toDeg(Math.asin(Math.sin(toRad(e)) * Math.sin(toRad(L))));
  function sunAngleTime(angle, ccw) {
    const cosHour = (-Math.sin(toRad(angle)) - Math.sin(toRad(decl)) * Math.sin(toRad(lat))) /
      (Math.cos(toRad(decl)) * Math.cos(toRad(lat)));
    if (Math.abs(cosHour) > 1) return null;
    const t = toDeg(Math.acos(cosHour)) / 15;
    return 12 - EqT + (ccw ? -t : t) - lng / 15 + timezone;
  }
  function asrTime(factor) {
    const a = toDeg(Math.atan(1 / (factor + Math.tan(toRad(Math.abs(lat - decl))))));
    return sunAngleTime(-a, false);
  }
  function toTime(t) {
    if (t == null) return "--:--";
    t = fixHour(t);
    return `${String(Math.floor(t)).padStart(2,'0')}:${String(Math.floor((t - Math.floor(t)) * 60)).padStart(2,'0')}`;
  }
  // Dzuhur = solar noon (langsung, bukan lewat sudut matahari)
  const dhuhr = 12 - EqT - lng / 15 + timezone;

  return {
    Imsak:   toTime(sunAngleTime(20, true) != null ? sunAngleTime(20, true) - 10/60 : null),
    Subuh:   toTime(sunAngleTime(20, true)),
    Syuruk:  toTime(sunAngleTime(-0.833, true)),
    Dzuhur:  toTime(dhuhr + 2/60), // +2 menit ikhtiyat
    Ashar:   toTime(asrTime(1)),
    Maghrib: toTime(sunAngleTime(-0.833, false)),
    Isya:    toTime(sunAngleTime(18, false)),
  };
}

// ─── Cities Database ─────────────────────────────────────────────────────────
const CITIES = [
  { province:"DKI Jakarta", cities:[
    {name:"Jakarta Pusat",lat:-6.1744,lng:106.8294,tz:7},
    {name:"Jakarta Selatan",lat:-6.2615,lng:106.8106,tz:7},
    {name:"Jakarta Barat",lat:-6.1682,lng:106.7632,tz:7},
    {name:"Jakarta Timur",lat:-6.2251,lng:106.9004,tz:7},
    {name:"Jakarta Utara",lat:-6.1209,lng:106.9005,tz:7},
  ]},
  { province:"Banten", cities:[
    {name:"Tangerang",lat:-6.1783,lng:106.6319,tz:7},
    {name:"Tangerang Selatan",lat:-6.2898,lng:106.7187,tz:7},
    {name:"Serang",lat:-6.1201,lng:106.1503,tz:7},
    {name:"Cilegon",lat:-6.0171,lng:106.0039,tz:7},
  ]},
  { province:"Jawa Barat", cities:[
    {name:"Bandung",lat:-6.9175,lng:107.6191,tz:7},
    {name:"Bekasi",lat:-6.2349,lng:106.9896,tz:7},
    {name:"Depok",lat:-6.4025,lng:106.7942,tz:7},
    {name:"Bogor",lat:-6.5971,lng:106.8060,tz:7},
    {name:"Cirebon",lat:-6.7320,lng:108.5523,tz:7},
    {name:"Sukabumi",lat:-6.9215,lng:106.9274,tz:7},
    {name:"Tasikmalaya",lat:-7.3274,lng:108.2207,tz:7},
    {name:"Karawang",lat:-6.3216,lng:107.3381,tz:7},
  ]},
  { province:"Jawa Tengah", cities:[
    {name:"Semarang",lat:-6.9932,lng:110.4203,tz:7},
    {name:"Solo (Surakarta)",lat:-7.5755,lng:110.8243,tz:7},
    {name:"Magelang",lat:-7.4797,lng:110.2177,tz:7},
    {name:"Salatiga",lat:-7.3306,lng:110.5080,tz:7},
    {name:"Pekalongan",lat:-6.8886,lng:109.6753,tz:7},
    {name:"Purwokerto",lat:-7.4210,lng:109.2345,tz:7},
    {name:"Kudus",lat:-6.8048,lng:110.8395,tz:7},
  ]},
  { province:"DI Yogyakarta", cities:[
    {name:"Yogyakarta",lat:-7.7956,lng:110.3695,tz:7},
    {name:"Sleman",lat:-7.7172,lng:110.3563,tz:7},
    {name:"Bantul",lat:-7.8916,lng:110.3295,tz:7},
    {name:"Gunungkidul",lat:-7.9524,lng:110.5935,tz:7},
  ]},
  { province:"Jawa Timur", cities:[
    {name:"Surabaya",lat:-7.2504,lng:112.7688,tz:7},
    {name:"Malang",lat:-7.9839,lng:112.6214,tz:7},
    {name:"Sidoarjo",lat:-7.4462,lng:112.7180,tz:7},
    {name:"Kediri",lat:-7.8235,lng:112.0115,tz:7},
    {name:"Madiun",lat:-7.6298,lng:111.5239,tz:7},
    {name:"Jember",lat:-8.1724,lng:113.7008,tz:7},
    {name:"Banyuwangi",lat:-8.2191,lng:114.3691,tz:7},
    {name:"Mojokerto",lat:-7.4723,lng:112.4337,tz:7},
  ]},
  { province:"Aceh", cities:[
    {name:"Banda Aceh",lat:5.5483,lng:95.3238,tz:7},
    {name:"Lhokseumawe",lat:5.1802,lng:97.1501,tz:7},
    {name:"Langsa",lat:4.4680,lng:97.9681,tz:7},
  ]},
  { province:"Sumatra Utara", cities:[
    {name:"Medan",lat:3.5952,lng:98.6722,tz:7},
    {name:"Binjai",lat:3.6003,lng:98.4854,tz:7},
    {name:"Pematangsiantar",lat:2.9595,lng:99.0687,tz:7},
    {name:"Tebing Tinggi",lat:3.3280,lng:99.1626,tz:7},
  ]},
  { province:"Sumatra Barat", cities:[
    {name:"Padang",lat:-0.9471,lng:100.4172,tz:7},
    {name:"Bukittinggi",lat:-0.3054,lng:100.3695,tz:7},
    {name:"Payakumbuh",lat:-0.2270,lng:100.6382,tz:7},
  ]},
  { province:"Riau", cities:[
    {name:"Pekanbaru",lat:0.5071,lng:101.4478,tz:7},
    {name:"Dumai",lat:1.6641,lng:101.4453,tz:7},
  ]},
  { province:"Kepulauan Riau", cities:[
    {name:"Batam",lat:1.1301,lng:104.0529,tz:7},
    {name:"Tanjung Pinang",lat:0.9189,lng:104.4653,tz:7},
  ]},
  { province:"Jambi", cities:[
    {name:"Jambi",lat:-1.6101,lng:103.6131,tz:7},
  ]},
  { province:"Sumatra Selatan", cities:[
    {name:"Palembang",lat:-2.9761,lng:104.7754,tz:7},
    {name:"Lubuklinggau",lat:-3.2998,lng:102.8620,tz:7},
    {name:"Prabumulih",lat:-3.4272,lng:104.2353,tz:7},
  ]},
  { province:"Bengkulu", cities:[
    {name:"Bengkulu",lat:-3.7928,lng:102.2608,tz:7},
  ]},
  { province:"Lampung", cities:[
    {name:"Bandar Lampung",lat:-5.3971,lng:105.2668,tz:7},
    {name:"Metro",lat:-5.1131,lng:105.3069,tz:7},
  ]},
  { province:"Kalimantan Barat", cities:[
    {name:"Pontianak",lat:-0.0263,lng:109.3425,tz:7},
    {name:"Singkawang",lat:0.9069,lng:108.9859,tz:7},
  ]},
  { province:"Kalimantan Tengah", cities:[
    {name:"Palangkaraya",lat:-2.2136,lng:113.9108,tz:7},
    {name:"Sampit",lat:-2.5372,lng:112.9525,tz:7},
  ]},
  { province:"Kalimantan Selatan", cities:[
    {name:"Banjarmasin",lat:-3.3194,lng:114.5908,tz:8},
    {name:"Banjarbaru",lat:-3.4420,lng:114.8306,tz:8},
    {name:"Martapura",lat:-3.4175,lng:114.8574,tz:8},
  ]},
  { province:"Kalimantan Timur", cities:[
    {name:"Samarinda",lat:-0.5022,lng:117.1536,tz:8},
    {name:"Balikpapan",lat:-1.2379,lng:116.8529,tz:8},
    {name:"Bontang",lat:0.1279,lng:117.5000,tz:8},
  ]},
  { province:"Kalimantan Utara", cities:[
    {name:"Tarakan",lat:3.3000,lng:117.6333,tz:8},
    {name:"Nunukan",lat:4.1354,lng:117.6663,tz:8},
  ]},
  { province:"Sulawesi Utara", cities:[
    {name:"Manado",lat:1.4748,lng:124.8421,tz:8},
    {name:"Bitung",lat:1.4474,lng:125.1931,tz:8},
    {name:"Tomohon",lat:1.3229,lng:124.8378,tz:8},
  ]},
  { province:"Sulawesi Tengah", cities:[
    {name:"Palu",lat:-0.8917,lng:119.8707,tz:8},
    {name:"Luwuk",lat:-0.9520,lng:122.7919,tz:8},
  ]},
  { province:"Sulawesi Selatan", cities:[
    {name:"Makassar",lat:-5.1477,lng:119.4327,tz:8},
    {name:"Parepare",lat:-4.0135,lng:119.6318,tz:8},
    {name:"Palopo",lat:-2.9930,lng:120.1943,tz:8},
    {name:"Gowa",lat:-5.2917,lng:119.5838,tz:8},
  ]},
  { province:"Sulawesi Tenggara", cities:[
    {name:"Kendari",lat:-3.9985,lng:122.5127,tz:8},
    {name:"Bau-bau",lat:-5.4679,lng:122.6068,tz:8},
  ]},
  { province:"Gorontalo", cities:[
    {name:"Gorontalo",lat:0.5435,lng:123.0568,tz:8},
  ]},
  { province:"Sulawesi Barat", cities:[
    {name:"Mamuju",lat:-2.6741,lng:118.8885,tz:8},
  ]},
  { province:"Bali", cities:[
    {name:"Denpasar",lat:-8.6705,lng:115.2126,tz:8},
    {name:"Singaraja",lat:-8.1116,lng:115.0892,tz:8},
    {name:"Tabanan",lat:-8.5362,lng:115.1253,tz:8},
  ]},
  { province:"Nusa Tenggara Barat", cities:[
    {name:"Mataram",lat:-8.5833,lng:116.1167,tz:8},
    {name:"Bima",lat:-8.4604,lng:118.7195,tz:8},
    {name:"Sumbawa Besar",lat:-8.4892,lng:117.4178,tz:8},
  ]},
  { province:"Nusa Tenggara Timur", cities:[
    {name:"Kupang",lat:-10.1772,lng:123.6071,tz:8},
    {name:"Ende",lat:-8.8432,lng:121.6620,tz:8},
    {name:"Maumere",lat:-8.6190,lng:122.2135,tz:8},
  ]},
  { province:"Maluku", cities:[
    {name:"Ambon",lat:-3.6954,lng:128.1814,tz:9},
    {name:"Ternate",lat:0.7833,lng:127.3667,tz:9},
    {name:"Tual",lat:-5.6389,lng:132.7500,tz:9},
  ]},
  { province:"Maluku Utara", cities:[
    {name:"Ternate",lat:0.7833,lng:127.3667,tz:9},
    {name:"Tidore",lat:0.6936,lng:127.4126,tz:9},
  ]},
  { province:"Papua Barat", cities:[
    {name:"Manokwari",lat:-0.8611,lng:134.0622,tz:9},
    {name:"Sorong",lat:-0.8817,lng:131.2617,tz:9},
  ]},
  { province:"Papua", cities:[
    {name:"Jayapura",lat:-2.5337,lng:140.7181,tz:9},
    {name:"Merauke",lat:-8.4957,lng:140.4018,tz:9},
    {name:"Timika",lat:-4.5333,lng:136.8833,tz:9},
  ]},
];

// ─── Content ──────────────────────────────────────────────────────────────────
const kajianData = [
  {id:1,title:"Keutamaan 10 Hari Pertama Ramadhan",category:"Amalan",date:"18 Feb 2026",readTime:"5 menit",excerpt:"Sepuluh hari pertama Ramadhan merupakan hari-hari penuh rahmat Allah SWT. Di saat inilah pintu-pintu langit terbuka lebar untuk menerima doa...",content:"Allah SWT telah membagi Ramadhan menjadi tiga bagian yang masing-masing memiliki keistimewaan. Sepuluh hari pertama adalah hari-hari yang Allah curahkan rahmat-Nya kepada seluruh hamba. Di saat inilah pintu-pintu langit terbuka lebar untuk menerima doa dan ibadah kita. Perbanyaklah shalat sunnah, tilawah Al-Qur'an, dan sedekah di hari-hari penuh berkah ini.",icon:"🌙",accent:"#d4af37"},
  {id:2,title:"Rahasia Lailatul Qadar yang Tersembunyi",category:"Ilmu",date:"17 Feb 2026",readTime:"7 menit",excerpt:"Lailatul Qadar adalah malam yang lebih baik dari seribu bulan. Malam ini tersembunyi di antara malam-malam ganjil sepuluh hari terakhir...",content:"Allah SWT merahasiakan malam Lailatul Qadar agar hamba-Nya bersungguh-sungguh mencarinya di setiap malam. Tanda-tandanya antara lain: udara yang sejuk, malam yang tenang, dan matahari yang terbit dengan sinar yang lemah lembut keesokan harinya. Rasulullah ﷺ menganjurkan untuk banyak berdoa dengan doa khusus Lailatul Qadar pada setiap malam ganjil di 10 hari terakhir.",icon:"✨",accent:"#a78bfa"},
  {id:3,title:"Panduan Lengkap I'tikaf di Masjid",category:"Fiqih",date:"16 Feb 2026",readTime:"8 menit",excerpt:"I'tikaf adalah berdiam diri di masjid dengan niat ibadah. Amalan ini sangat dianjurkan terutama pada 10 hari terakhir Ramadhan...",content:"I'tikaf memiliki syarat-syarat tertentu: berakal, suci dari hadas besar, dan berada di masjid. Selama i'tikaf, dianjurkan memperbanyak dzikir, doa, tilawah, dan menjauhi hal-hal yang tidak bermanfaat. Nabi ﷺ senantiasa beri'tikaf pada sepuluh hari terakhir Ramadhan hingga beliau wafat.",icon:"🕌",accent:"#34d399"},
  {id:4,title:"Menghidupkan Malam dengan Qiyamul Lail",category:"Amalan",date:"15 Feb 2026",readTime:"4 menit",excerpt:"Shalat malam di bulan Ramadhan memiliki keutamaan yang luar biasa. Barang siapa mendirikannya dengan iman dan ikhlas...",content:"Qiyamul Lail atau shalat malam di bulan Ramadhan bisa dilakukan mulai dari dua rakaat hingga sebelas rakaat (witir termasuk). Waktu terbaiknya adalah sepertiga malam terakhir, sekitar pukul 02.00-03.30 WIB. Rasulullah ﷺ bersabda: 'Barang siapa mendirikan shalat malam di bulan Ramadhan karena iman dan mengharap pahala, maka diampuni dosa-dosanya yang telah lalu.'",icon:"🌟",accent:"#60a5fa"},
  {id:5,title:"Adab dan Sunnah Berbuka Puasa",category:"Sunnah",date:"14 Feb 2026",readTime:"3 menit",excerpt:"Berbuka puasa adalah salah satu kegembiraan bagi orang yang berpuasa. Terdapat beberapa adab yang diajarkan Rasulullah ﷺ...",content:"Sunnah berbuka puasa: menyegerakan berbuka begitu azan maghrib berkumandang, berbuka dengan kurma atau air, membaca doa berbuka, dan makan secukupnya agar tidak berlebihan. Rasulullah ﷺ bersabda: 'Manusia senantiasa dalam kebaikan selama mereka menyegerakan berbuka.'",icon:"🌅",accent:"#fb923c"},
];

const doaData = [
  {id:1,title:"Doa Berbuka Puasa",arabic:"اللَّهُمَّ لَكَ صُمْتُ وَبِكَ آمَنْتُ وَعَلَى رِزْقِكَ أَفْطَرْتُ",latin:"Allahumma laka shumtu wa bika aamantu wa 'ala rizqika afthartu",arti:"Ya Allah, karena-Mu aku berpuasa, kepada-Mu aku beriman, dan dengan rezeki-Mu aku berbuka."},
  {id:2,title:"Doa Niat Puasa",arabic:"نَوَيْتُ صَوْمَ غَدٍ عَنْ أَدَاءِ فَرْضِ شَهْرِ رَمَضَانَ هَذِهِ السَّنَةِ لِلهِ تَعَالَى",latin:"Nawaitu shauma ghadin 'an adaa'i fardhi syahri Ramadhana haadzihis sanati lillahi ta'alaa",arti:"Saya niat berpuasa esok hari untuk menunaikan kewajiban puasa di bulan Ramadhan tahun ini karena Allah Ta'ala."},
  {id:3,title:"Doa Lailatul Qadar",arabic:"اللَّهُمَّ إِنَّكَ عَفُوٌّ تُحِبُّ الْعَفْوَ فَاعْفُ عَنِّي",latin:"Allahumma innaka 'afuwwun tuhibbul 'afwa fa'fu 'anni",arti:"Ya Allah, sesungguhnya Engkau Maha Pemaaf dan mencintai maaf, maka maafkanlah aku."},
  {id:4,title:"Doa Setelah Sahur",arabic:"وَبِصَوْمِ غَدٍ نَّوَيْتُ مِنْ شَهْرِ رَمَضَانَ",latin:"Wa bishaumi ghadin nawaytu min syahri Ramadhana",arti:"Dan aku berniat puasa esok hari dari bulan Ramadhan."},
  {id:5,title:"Doa Khatam Al-Quran",arabic:"اللَّهُمَّ ارْحَمْنِي بِالْقُرْآنِ وَاجْعَلْهُ لِي إِمَامًا وَنُورًا وَهُدًى وَرَحْمَةً",latin:"Allahummarhamni bil Qur'an waj'alhu li imaaman wa nuuran wa hudaw wa rahmatan",arti:"Ya Allah, rahmatilah aku dengan Al-Qur'an dan jadikan ia untukku pemimpin, cahaya, petunjuk, dan rahmat."},
  {id:6,title:"Doa Malam Ganjil",arabic:"اللَّهُمَّ إِنَّكَ عَفُوٌّ كَرِيمٌ تُحِبُّ الْعَفْوَ فَاعْفُ عَنَّا",latin:"Allahumma innaka 'afuwwun kariim tuhibbul 'afwa fa'fu 'anna",arti:"Ya Allah, sesungguhnya Engkau Maha Pemaaf lagi Maha Mulia, mencintai maaf, maka maafkanlah kami."},
];

const PRAYER_ICONS = {Imsak:"🌙",Subuh:"🌅",Syuruk:"☀️",Dzuhur:"🌤️",Ashar:"⛅",Maghrib:"🌇",Isya:"🌃"};
const MONTHS_ID = ["Januari","Februari","Maret","April","Mei","Juni","Juli","Agustus","September","Oktober","November","Desember"];

function getHijri() {
  try { return new Intl.DateTimeFormat('id-ID-u-ca-islamic-umalqura',{day:'numeric',month:'long',year:'numeric'}).format(new Date()); }
  catch { return "Sya'ban 1447 H"; }
}

// ─── Theme ────────────────────────────────────────────────────────────────────
const THEMES = {
  dark: {
    bg:'#0a0f1a', bg2:'#111827',
    card:'rgba(255,255,255,0.045)', cardB:'rgba(255,255,255,0.09)',
    text:'#f0ede6', textSub:'rgba(240,237,230,0.55)', textMute:'rgba(240,237,230,0.32)',
    nav:'rgba(8,13,24,0.96)', navB:'rgba(212,175,55,0.15)',
    input:'rgba(255,255,255,0.07)', inputB:'rgba(255,255,255,0.13)',
    div:'rgba(255,255,255,0.06)',
    heroBg:'linear-gradient(135deg,#0d1a2e 0%,#162035 50%,#0f1e0e 100%)',
    gold:'#d4af37', goldText:'#f5e198', goldDim:'rgba(212,175,55,0.8)',
    accent:'rgba(212,175,55,0.15)', accentB:'rgba(212,175,55,0.35)',
    modalBg:'#0d1728', modalCard:'rgba(255,255,255,0.04)',
    switchBg:'rgba(212,175,55,0.25)', switchKnob:'#d4af37', switchOn:true,
    prov:'rgba(255,255,255,0.025)', provActive:'rgba(255,255,255,0.05)',
    countdownColor:'#f5e198',
    geo:"rgba(212,175,55,0.06)",
    progressBg:'rgba(255,255,255,0.09)',
    blueBg:'rgba(32,100,180,0.14)', blueB:'rgba(100,150,255,0.15)',
    greenBg:'rgba(20,80,45,0.22)', greenB:'rgba(32,178,95,0.17)',
    subuhGradient:'rgba(212,175,55,0.09)',
    sectionLabelColor:'rgba(240,237,230,0.38)',
  },
  light: {
    bg:'#f7f2e8', bg2:'#fefcf7',
    card:'rgba(255,255,255,0.88)', cardB:'rgba(180,140,50,0.16)',
    text:'#1c1408', textSub:'rgba(28,20,8,0.58)', textMute:'rgba(28,20,8,0.36)',
    nav:'rgba(251,248,240,0.97)', navB:'rgba(180,140,50,0.22)',
    input:'rgba(255,255,255,0.75)', inputB:'rgba(160,120,40,0.22)',
    div:'rgba(160,120,40,0.1)',
    heroBg:'linear-gradient(135deg,#fffdf4 0%,#fffaec 50%,#f7f4e4 100%)',
    gold:'#b37f00', goldText:'#8a6000', goldDim:'rgba(140,100,0,0.85)',
    accent:'rgba(180,140,50,0.1)', accentB:'rgba(160,120,40,0.3)',
    modalBg:'#fefcf7', modalCard:'rgba(0,0,0,0.025)',
    switchBg:'rgba(160,120,40,0.18)', switchKnob:'#b37f00', switchOn:false,
    prov:'rgba(0,0,0,0.02)', provActive:'rgba(0,0,0,0.04)',
    countdownColor:'#8a6000',
    geo:"rgba(160,120,40,0.08)",
    progressBg:'rgba(0,0,0,0.08)',
    blueBg:'rgba(32,100,180,0.07)', blueB:'rgba(100,150,255,0.18)',
    greenBg:'rgba(20,120,60,0.08)', greenB:'rgba(32,160,80,0.18)',
    subuhGradient:'rgba(180,140,50,0.07)',
    sectionLabelColor:'rgba(28,20,8,0.4)',
  }
};

const SURAH_LIST = [
  {no:1,name:"Al-Fatihah",ar:"الفاتحة",ayat:7,juz:1},
  {no:2,name:"Al-Baqarah",ar:"البقرة",ayat:286,juz:1},
  {no:3,name:"Ali 'Imran",ar:"آل عمران",ayat:200,juz:3},
  {no:4,name:"An-Nisa",ar:"النساء",ayat:176,juz:4},
  {no:5,name:"Al-Ma'idah",ar:"المائدة",ayat:120,juz:6},
  {no:6,name:"Al-An'am",ar:"الأنعام",ayat:165,juz:7},
  {no:7,name:"Al-A'raf",ar:"الأعراف",ayat:206,juz:8},
  {no:8,name:"Al-Anfal",ar:"الأنفال",ayat:75,juz:9},
  {no:9,name:"At-Taubah",ar:"التوبة",ayat:129,juz:10},
  {no:10,name:"Yunus",ar:"يونس",ayat:109,juz:11},
  {no:36,name:"Yasin",ar:"يس",ayat:83,juz:22},
  {no:55,name:"Ar-Rahman",ar:"الرحمن",ayat:78,juz:27},
  {no:67,name:"Al-Mulk",ar:"الملك",ayat:30,juz:29},
  {no:112,name:"Al-Ikhlas",ar:"الإخلاص",ayat:4,juz:30},
  {no:113,name:"Al-Falaq",ar:"الفلق",ayat:5,juz:30},
  {no:114,name:"An-Nas",ar:"الناس",ayat:6,juz:30},
];

export default function RamadanApp() {
  const [isDark, setIsDark] = useState(true);
  const T = isDark ? THEMES.dark : THEMES.light;

  const [tab, setTab] = useState("home");
  const [loc, setLoc] = useState(CITIES[1].cities[0]); // Tangerang
  const [times, setTimes] = useState(null);
  const [now, setNow] = useState(new Date());
  const [countdown, setCountdown] = useState("00:00:00");
  const [nextPrayer, setNextPrayer] = useState("");
  const [selKajian, setSelKajian] = useState(null);
  const [selDoa, setSelDoa] = useState(null);
  const [copiedId, setCopiedId] = useState(null);
  const [showLoc, setShowLoc] = useState(false);
  const [locQ, setLocQ] = useState("");
  const [expProv, setExpProv] = useState(null);
  const [ramDay, setRamDay] = useState(null);
  const [themeFlash, setThemeFlash] = useState(false);

  useEffect(() => {
    const start = new Date(2026,1,28);
    const diff = Math.floor((new Date() - start) / 86400000);
    setRamDay(diff >= 0 && diff < 30 ? diff+1 : null);
  }, []);

  useEffect(() => {
    const d = new Date();
    setTimes(calcPrayerTimes(d.getFullYear(), d.getMonth()+1, d.getDate(), loc.lat, loc.lng, loc.tz));
  }, [loc]);

  useEffect(() => {
    const tick = setInterval(() => {
      const n = new Date();
      setNow(n);
      if (!times) return;
      const ORDER = ["Imsak","Subuh","Dzuhur","Ashar","Maghrib","Isya"];
      const cur = n.getHours()*60 + n.getMinutes();
      let next = ORDER.find(p => { const [h,m]=times[p].split(":").map(Number); return h*60+m > cur; });
      if (!next) next = "Imsak";
      setNextPrayer(next);
      const [nh,nm] = (() => {
        if (next === "Imsak") { const [h,m]=times["Imsak"].split(":").map(Number); return [h+24,m]; }
        return times[next].split(":").map(Number);
      })();
      const diff = (nh*60+nm) - cur;
      const h=Math.floor(diff/60), m=diff%60, s=59-n.getSeconds();
      setCountdown(`${String(h).padStart(2,'0')}:${String(m).padStart(2,'0')}:${String(s).padStart(2,'0')}`);
    }, 1000);
    return () => clearInterval(tick);
  }, [times]);

  function toggleTheme() {
    setThemeFlash(true);
    setTimeout(() => setThemeFlash(false), 350);
    setIsDark(d => !d);
  }

  const todayStr = `${now.getDate()} ${MONTHS_ID[now.getMonth()]} ${now.getFullYear()}`;
  const clockStr = `${String(now.getHours()).padStart(2,'0')}:${String(now.getMinutes()).padStart(2,'0')}:${String(now.getSeconds()).padStart(2,'0')}`;
  const isNext = n => n === nextPrayer;

  const jadwal30 = Array.from({length:30},(_,i)=>{
    const d = new Date(2026,1,28+i);
    const t = calcPrayerTimes(d.getFullYear(),d.getMonth()+1,d.getDate(),loc.lat,loc.lng,loc.tz);
    return {day:i+1,date:`${d.getDate()} ${MONTHS_ID[d.getMonth()]}`,imsak:t.Imsak,subuh:t.Subuh,maghrib:t.Maghrib,isya:t.Isya};
  });

  const filtered = locQ.trim()
    ? CITIES.flatMap(p=>p.cities.filter(c=>c.name.toLowerCase().includes(locQ.toLowerCase())).map(c=>({...c,province:p.province})))
    : [];

  function copyDoa(doa) {
    navigator.clipboard.writeText(`${doa.arabic}\n\n${doa.latin}\n\nArtinya: ${doa.arti}`).then(()=>{
      setCopiedId(doa.id); setTimeout(()=>setCopiedId(null),2000);
    });
  }

  const geoSvg = `url("data:image/svg+xml,%3Csvg width='60' height='60' viewBox='0 0 60 60' xmlns='http://www.w3.org/2000/svg'%3E%3Cg fill='none' stroke='${encodeURIComponent(T.geo)}' stroke-width='1'%3E%3Cpolygon points='30,2 58,17 58,43 30,58 2,43 2,17'/%3E%3Cpolygon points='30,12 48,22 48,38 30,48 12,38 12,22'/%3E%3C/g%3E%3C/svg%3E")`;

  return (
    <>
      <style>{`
        @import url('https://fonts.googleapis.com/css2?family=Amiri:wght@400;700&family=Outfit:wght@300;400;500;600;700&display=swap');
        *{box-sizing:border-box;-webkit-tap-highlight-color:transparent}
        html,body{margin:0;padding:0;background:${T.bg}}
        ::-webkit-scrollbar{display:none}
        .app{font-family:'Outfit',sans-serif;background:${T.bg};min-height:100vh;max-width:430px;margin:0 auto;position:relative;transition:background 0.3s}
        .arabic{font-family:'Amiri',serif;direction:rtl;text-align:right;line-height:2.1}
        .scr{overflow-y:auto;-webkit-overflow-scrolling:touch;height:calc(100vh - 112px);padding-bottom:86px}
        .fi{animation:fi 0.35s ease}
        @keyframes fi{from{opacity:0;transform:translateY(8px)}to{opacity:1;transform:translateY(0)}}
        .pr{transition:transform 0.14s,opacity 0.14s;cursor:pointer}
        .pr:active{transform:scale(0.96);opacity:0.82}
        .bnav{position:fixed;bottom:0;left:50%;transform:translateX(-50%);width:100%;max-width:430px;background:${T.nav};backdrop-filter:blur(22px);border-top:1px solid ${T.navB};z-index:100;padding:10px 0 16px}
        .tflash{animation:tfl 0.35s ease}
        @keyframes tfl{0%{opacity:1}40%{opacity:0.65}100%{opacity:1}}
        .moverlay{position:fixed;inset:0;background:rgba(0,0,0,0.55);backdrop-filter:blur(5px);z-index:200;display:flex;align-items:flex-end;justify-content:center}
        .msheet{background:${T.modalBg};border-radius:24px 24px 0 0;width:100%;max-width:430px;max-height:88vh;display:flex;flex-direction:column}
        .provrow{transition:background 0.12s;cursor:pointer}
        .provrow:active{background:${T.provActive}!important}
        input{font-family:'Outfit',sans-serif;outline:none}
        input::placeholder{color:${T.textMute}}
        .sw-track{width:46px;height:26px;border-radius:13px;background:${T.switchBg};position:relative;cursor:pointer;border:1px solid ${isDark?'rgba(212,175,55,0.35)':'rgba(160,120,40,0.28)'};transition:background 0.3s,border 0.3s}
        .sw-knob{width:20px;height:20px;border-radius:50%;background:${T.switchKnob};position:absolute;top:2px;left:${isDark?'22px':'2px'};transition:left 0.28s cubic-bezier(0.4,0,0.2,1);box-shadow:0 1px 5px rgba(0,0,0,0.28)}
        .slabel{font-size:10px;letter-spacing:2px;text-transform:uppercase;color:${T.sectionLabelColor};margin:0 0 10px 4px;font-weight:600}
        .bar{height:7px;border-radius:5px;overflow:hidden;background:${T.progressBg}}
        .bar-fill{height:100%;border-radius:5px;background:linear-gradient(90deg,#60a5fa,#93c5fd);transition:width 0.9s ease}
        .topbar{position:sticky;top:0;z-index:50;background:${isDark?'rgba(8,13,24,0.94)':'rgba(250,247,240,0.94)'};backdrop-filter:blur(22px);border-bottom:1px solid ${T.navB};padding:10px 18px 10px;display:flex;justify-content:space-between;align-items:center}
      `}</style>

      <div className={`app${themeFlash?' tflash':''}`} style={{backgroundImage:geoSvg}}>

        {/* ─── Top Bar ─── */}
        <div className="topbar">
          <span style={{color:T.goldDim,fontSize:12,fontWeight:700,letterSpacing:0.5}}>☪ Ramadan 1447H</span>
          <div style={{display:'flex',alignItems:'center',gap:12}}>
            <span style={{color:T.textMute,fontSize:11,fontFamily:'monospace'}}>{clockStr}</span>
            <div style={{display:'flex',alignItems:'center',gap:6}}>
              <span style={{fontSize:14}}>{isDark?'🌙':'☀️'}</span>
              <div className="sw-track" onClick={toggleTheme}><div className="sw-knob"/></div>
            </div>
          </div>
        </div>

        {/* ════════════════════ HOME ════════════════════ */}
        {tab==="home" && (
          <div className="scr fi" style={{padding:'0 16px 20px'}}>

            {/* Hero */}
            <div style={{borderRadius:24,overflow:'hidden',margin:'14px 0 14px',background:T.heroBg,border:`1px solid ${T.accentB}`,padding:22,position:'relative'}}>
              <div style={{position:'absolute',top:-24,right:-24,width:120,height:120,borderRadius:'50%',background:`radial-gradient(circle,${isDark?'rgba(212,175,55,0.12)':'rgba(212,175,55,0.1)'} 0%,transparent 70%)`}}/>
              <div style={{display:'flex',justifyContent:'space-between',alignItems:'flex-start',marginBottom:14}}>
                <div>
                  <p style={{margin:0,color:T.textMute,fontSize:11,letterSpacing:1.5}}>{todayStr}</p>
                  <p style={{margin:'3px 0 0',color:T.goldDim,fontSize:11}}>{getHijri()}</p>
                </div>
                <button onClick={()=>setShowLoc(true)} className="pr" style={{display:'flex',alignItems:'center',gap:5,background:isDark?'rgba(255,255,255,0.07)':'rgba(0,0,0,0.05)',border:`1px solid ${T.cardB}`,borderRadius:12,padding:'6px 11px',cursor:'pointer'}}>
                  <span style={{fontSize:12}}>📍</span>
                  <span style={{color:T.textSub,fontSize:11,fontWeight:500,maxWidth:90,overflow:'hidden',textOverflow:'ellipsis',whiteSpace:'nowrap'}}>{loc.name}</span>
                  <span style={{color:T.gold,fontSize:10}}>▾</span>
                </button>
              </div>
              <div style={{textAlign:'center',padding:'6px 0 6px'}}>
                <p style={{margin:'0 0 5px',color:T.textSub,fontSize:12}}>
                  {nextPrayer==="Maghrib"?"⏳ Menuju Waktu Berbuka":nextPrayer==="Imsak"?"⏳ Menuju Imsak":`⏳ Menuju ${nextPrayer}`}
                </p>
                <div style={{fontFamily:'monospace',fontSize:44,fontWeight:700,color:T.countdownColor,letterSpacing:2,textShadow:isDark?'0 0 26px rgba(212,175,55,0.3)':'none'}}>
                  {countdown}
                </div>
                {ramDay && (
                  <div style={{marginTop:12}}>
                    <span style={{background:T.accent,border:`1px solid ${T.accentB}`,borderRadius:20,padding:'4px 14px',color:T.gold,fontSize:11,fontWeight:700}}>
                      Ramadan Hari ke-{ramDay}
                    </span>
                  </div>
                )}
              </div>
            </div>

            {/* Quick prayer */}
            <p className="slabel">Jadwal Hari Ini</p>
            <div style={{display:'grid',gridTemplateColumns:'1fr 1fr',gap:10,marginBottom:16}}>
              {times && ["Imsak","Subuh","Maghrib","Isya"].map(name=>(
                <div key={name} className="pr" style={{borderRadius:18,padding:'14px 15px',background:isNext(name)?T.accent:T.card,border:`1px solid ${isNext(name)?T.accentB:T.cardB}`}}>
                  <div style={{display:'flex',justifyContent:'space-between',alignItems:'center'}}>
                    <span style={{fontSize:18}}>{PRAYER_ICONS[name]}</span>
                    {isNext(name) && <span style={{background:T.gold,borderRadius:6,padding:'2px 7px',fontSize:8,fontWeight:800,color:'#0a0f1a'}}>NEXT</span>}
                  </div>
                  <p style={{margin:'8px 0 2px',color:T.textSub,fontSize:11}}>{name}</p>
                  <p style={{margin:0,color:isNext(name)?T.countdownColor:T.text,fontSize:22,fontWeight:700}}>{times[name]}</p>
                </div>
              ))}
            </div>

            {/* Amalan */}
            <p className="slabel">Amalan Harian</p>
            <div style={{borderRadius:20,background:T.card,border:`1px solid ${T.cardB}`,marginBottom:16,overflow:'hidden'}}>
              {[{i:"📖",l:"Tilawah Al-Qur'an",s:"1 Juz per hari"},{i:"🤲",l:"Dzikir Pagi & Petang",s:"Setelah Subuh & Ashar"},{i:"💝",l:"Sedekah Harian",s:"Walau sedikit"},{i:"🕌",l:"Shalat Tarawih",s:"Berjamaah di masjid"}]
                .map((it,idx,arr)=>(
                <div key={idx} style={{display:'flex',alignItems:'center',padding:'13px 16px',borderBottom:idx<arr.length-1?`1px solid ${T.div}`:'none'}}>
                  <span style={{fontSize:20,marginRight:13}}>{it.i}</span>
                  <div style={{flex:1}}>
                    <p style={{margin:0,color:T.text,fontSize:13,fontWeight:500}}>{it.l}</p>
                    <p style={{margin:'1px 0 0',color:T.textMute,fontSize:11}}>{it.s}</p>
                  </div>
                  <div style={{width:22,height:22,borderRadius:'50%',border:`2px solid ${T.accentB}`}}/>
                </div>
              ))}
            </div>

            {/* Ayat */}
            <div style={{borderRadius:20,background:T.greenBg,border:`1px solid ${T.greenB}`,padding:'18px 20px',textAlign:'center'}}>
              <p className="arabic" style={{color:T.goldDim,fontSize:19,margin:'0 0 10px',lineHeight:1.9}}>شَهْرُ رَمَضَانَ الَّذِي أُنزِلَ فِيهِ الْقُرْآنُ</p>
              <p style={{color:T.textSub,fontSize:12,margin:0,fontStyle:'italic',lineHeight:1.6}}>"Bulan Ramadhan yang di dalamnya diturunkan Al-Qur'an..." — QS. Al-Baqarah: 185</p>
            </div>
          </div>
        )}

        {/* ════════════════════ JADWAL ════════════════════ */}
        {tab==="jadwal" && (
          <div className="scr fi" style={{padding:'0 16px 20px'}}>
            <div style={{padding:'14px 0 12px',display:'flex',justifyContent:'space-between',alignItems:'center'}}>
              <div>
                <h2 style={{margin:0,color:T.text,fontSize:21,fontWeight:700}}>Jadwal Sholat</h2>
                <button onClick={()=>setShowLoc(true)} className="pr" style={{display:'flex',alignItems:'center',gap:4,background:'none',border:'none',cursor:'pointer',padding:0,marginTop:4}}>
                  <span style={{color:T.goldDim,fontSize:12}}>📍 {loc.name}</span>
                  <span style={{color:T.gold,fontSize:10}}>▾</span>
                </button>
              </div>
              <span style={{background:T.accent,border:`1px solid ${T.accentB}`,borderRadius:10,padding:'5px 11px',color:T.gold,fontSize:11,fontWeight:600}}>
                WIB{loc.tz>7?`+${loc.tz-7}`:''}
              </span>
            </div>

            {times && (
              <div style={{borderRadius:20,overflow:'hidden',border:`1px solid ${T.cardB}`,marginBottom:14}}>
                <div style={{padding:'12px 16px',background:T.subuhGradient,borderBottom:`1px solid ${T.div}`}}>
                  <span style={{color:T.gold,fontWeight:600,fontSize:12}}>Hari Ini — {todayStr}</span>
                </div>
                {Object.entries(times).map(([name,time],i,arr)=>(
                  <div key={name} style={{display:'flex',alignItems:'center',padding:'13px 16px',background:isNext(name)?(isDark?'rgba(212,175,55,0.07)':'rgba(180,140,50,0.06)'):'transparent',borderBottom:i<arr.length-1?`1px solid ${T.div}`:'none'}}>
                    <span style={{fontSize:18,marginRight:11,width:26,textAlign:'center'}}>{PRAYER_ICONS[name]||'🌙'}</span>
                    <span style={{flex:1,color:isNext(name)?T.countdownColor:T.text,fontSize:14,fontWeight:isNext(name)?600:400}}>{name}</span>
                    {isNext(name) && <span style={{background:T.gold,borderRadius:5,padding:'2px 7px',fontSize:8,fontWeight:700,color:'#0a0f1a',marginRight:10}}>NEXT</span>}
                    <span style={{color:isNext(name)?T.countdownColor:T.text,fontSize:15,fontWeight:600,fontFamily:'monospace'}}>{time}</span>
                  </div>
                ))}
              </div>
            )}

            <p className="slabel">Jadwal 30 Hari Ramadan 1447H</p>
            <div style={{borderRadius:18,overflow:'hidden',border:`1px solid ${T.cardB}`}}>
              <div style={{display:'grid',gridTemplateColumns:'30px 1fr 56px 56px 60px',padding:'10px 13px',background:T.subuhGradient,borderBottom:`1px solid ${T.div}`}}>
                {["#","Tanggal","Imsak","Subuh","Buka"].map(h=>(
                  <span key={h} style={{color:T.gold,fontSize:9,fontWeight:700,letterSpacing:0.5}}>{h}</span>
                ))}
              </div>
              {jadwal30.map((row,i)=>{
                const today = ramDay===row.day;
                return (
                  <div key={i} style={{display:'grid',gridTemplateColumns:'30px 1fr 56px 56px 60px',padding:'10px 13px',background:today?T.accent:(i%2===0?'transparent':(isDark?'rgba(255,255,255,0.014)':'rgba(0,0,0,0.014)')),borderBottom:`1px solid ${T.div}`}}>
                    <span style={{color:today?T.gold:T.textMute,fontSize:11,fontWeight:today?700:400}}>{row.day}</span>
                    <span style={{color:today?T.countdownColor:T.textSub,fontSize:11,fontWeight:today?600:400}}>{row.date}</span>
                    <span style={{color:T.textSub,fontSize:11,fontFamily:'monospace'}}>{row.imsak}</span>
                    <span style={{color:T.textSub,fontSize:11,fontFamily:'monospace'}}>{row.subuh}</span>
                    <span style={{color:isDark?'#f59e0b':'#b45309',fontSize:11,fontFamily:'monospace',fontWeight:600}}>{row.maghrib}</span>
                  </div>
                );
              })}
            </div>
          </div>
        )}

        {/* ════════════════════ KAJIAN ════════════════════ */}
        {tab==="kajian" && !selKajian && (
          <div className="scr fi" style={{padding:'0 16px 20px'}}>
            <div style={{padding:'14px 0 12px'}}>
              <h2 style={{margin:0,color:T.text,fontSize:21,fontWeight:700}}>Blog Kajian</h2>
              <p style={{margin:'3px 0 0',color:T.textMute,fontSize:12}}>Ilmu perbekalan Ramadhan</p>
            </div>
            {kajianData.map(item=>(
              <div key={item.id} className="pr" onClick={()=>setSelKajian(item)} style={{borderRadius:20,overflow:'hidden',marginBottom:13,border:`1px solid ${T.cardB}`,background:T.card}}>
                <div style={{padding:'17px 17px 13px',borderBottom:`1px solid ${T.div}`}}>
                  <div style={{display:'flex',justifyContent:'space-between',alignItems:'center',marginBottom:8}}>
                    <span style={{fontSize:26}}>{item.icon}</span>
                    <span style={{background:isDark?'rgba(255,255,255,0.07)':'rgba(0,0,0,0.06)',borderRadius:10,padding:'3px 10px',color:T.textSub,fontSize:10,fontWeight:600}}>{item.category}</span>
                  </div>
                  <h3 style={{margin:0,color:T.text,fontSize:15,fontWeight:700,lineHeight:1.4}}>{item.title}</h3>
                </div>
                <div style={{padding:'12px 17px'}}>
                  <p style={{margin:'0 0 9px',color:T.textSub,fontSize:12,lineHeight:1.7}}>{item.excerpt}</p>
                  <div style={{display:'flex',justifyContent:'space-between'}}>
                    <span style={{color:T.textMute,fontSize:11}}>📅 {item.date} · ⏱ {item.readTime}</span>
                    <span style={{color:T.gold,fontSize:12,fontWeight:600}}>Baca →</span>
                  </div>
                </div>
              </div>
            ))}
          </div>
        )}
        {tab==="kajian" && selKajian && (
          <div className="scr fi" style={{padding:'0 16px 20px'}}>
            <button onClick={()=>setSelKajian(null)} className="pr" style={{background:T.card,border:`1px solid ${T.cardB}`,borderRadius:12,color:T.text,padding:'9px 15px',marginTop:14,marginBottom:14,fontSize:12,cursor:'pointer',fontFamily:'Outfit,sans-serif'}}>← Kembali</button>
            <div style={{borderRadius:20,overflow:'hidden',border:`1px solid ${T.cardB}`}}>
              <div style={{padding:'20px 20px 15px',borderBottom:`1px solid ${T.div}`}}>
                <div style={{display:'flex',alignItems:'center',gap:10,marginBottom:11}}>
                  <span style={{fontSize:28}}>{selKajian.icon}</span>
                  <span style={{background:T.accent,border:`1px solid ${T.accentB}`,borderRadius:10,padding:'3px 11px',color:T.gold,fontSize:10,fontWeight:700}}>{selKajian.category}</span>
                </div>
                <h2 style={{margin:'0 0 7px',color:T.text,fontSize:18,fontWeight:700,lineHeight:1.4}}>{selKajian.title}</h2>
                <p style={{margin:0,color:T.textMute,fontSize:11}}>📅 {selKajian.date} · ⏱ {selKajian.readTime}</p>
              </div>
              <div style={{padding:'18px 20px',background:T.card}}>
                <p style={{margin:0,color:T.textSub,fontSize:14,lineHeight:1.85}}>{selKajian.content}</p>
              </div>
            </div>
          </div>
        )}

        {/* ════════════════════ DOA ════════════════════ */}
        {tab==="doa" && !selDoa && (
          <div className="scr fi" style={{padding:'0 16px 20px'}}>
            <div style={{padding:'14px 0 12px'}}>
              <h2 style={{margin:0,color:T.text,fontSize:21,fontWeight:700}}>Kumpulan Doa</h2>
              <p style={{margin:'3px 0 0',color:T.textMute,fontSize:12}}>Doa-doa pilihan Ramadhan</p>
            </div>
            {doaData.map(doa=>(
              <div key={doa.id} className="pr" onClick={()=>setSelDoa(doa)} style={{borderRadius:18,padding:'15px',marginBottom:11,background:T.card,border:`1px solid ${T.cardB}`}}>
                <div style={{display:'flex',justifyContent:'space-between',alignItems:'center',marginBottom:8}}>
                  <span style={{color:T.text,fontSize:14,fontWeight:600}}>{doa.title}</span>
                  <span style={{color:T.gold,fontSize:16}}>›</span>
                </div>
                <p className="arabic" style={{color:T.goldDim,fontSize:15,margin:'0 0 7px',lineHeight:1.9}}>{doa.arabic.substring(0,50)}...</p>
                <p style={{color:T.textMute,fontSize:11,margin:0,fontStyle:'italic'}}>{doa.arti.substring(0,68)}...</p>
              </div>
            ))}
          </div>
        )}
        {tab==="doa" && selDoa && (
          <div className="scr fi" style={{padding:'0 16px 20px'}}>
            <button onClick={()=>setSelDoa(null)} className="pr" style={{background:T.card,border:`1px solid ${T.cardB}`,borderRadius:12,color:T.text,padding:'9px 15px',marginTop:14,marginBottom:14,fontSize:12,cursor:'pointer',fontFamily:'Outfit,sans-serif'}}>← Kembali</button>
            <div style={{borderRadius:20,overflow:'hidden',border:`1px solid ${T.accentB}`}}>
              <div style={{padding:'17px 20px 13px',background:T.accent}}>
                <h3 style={{margin:0,color:T.countdownColor,fontSize:17,fontWeight:700}}>{selDoa.title}</h3>
              </div>
              <div style={{padding:'19px',background:T.card}}>
                <div style={{background:isDark?'rgba(212,175,55,0.06)':'rgba(212,175,55,0.07)',borderRadius:15,padding:'17px 14px',marginBottom:14,border:`1px solid ${T.accentB}`}}>
                  <p className="arabic" style={{color:T.goldDim,fontSize:21,margin:0,lineHeight:2.1}}>{selDoa.arabic}</p>
                </div>
                <div style={{marginBottom:13}}>
                  <p style={{color:T.textMute,fontSize:9,letterSpacing:1.5,textTransform:'uppercase',margin:'0 0 5px',fontWeight:600}}>Latin</p>
                  <p style={{color:T.textSub,fontSize:13,margin:0,lineHeight:1.75,fontStyle:'italic'}}>{selDoa.latin}</p>
                </div>
                <div style={{marginBottom:17}}>
                  <p style={{color:T.textMute,fontSize:9,letterSpacing:1.5,textTransform:'uppercase',margin:'0 0 5px',fontWeight:600}}>Artinya</p>
                  <p style={{color:T.text,fontSize:13,margin:0,lineHeight:1.75}}>{selDoa.arti}</p>
                </div>
                <button onClick={()=>copyDoa(selDoa)} className="pr" style={{width:'100%',padding:'13px',borderRadius:13,border:'none',background:copiedId===selDoa.id?(isDark?'rgba(52,211,153,0.18)':'rgba(32,160,80,0.13)'):(isDark?'rgba(212,175,55,0.14)':'rgba(180,140,50,0.11)'),color:copiedId===selDoa.id?'#34d399':T.gold,fontSize:13,fontWeight:600,cursor:'pointer',fontFamily:'Outfit,sans-serif',transition:'all 0.2s'}}>
                  {copiedId===selDoa.id ? "✓ Berhasil Disalin!" : "📋 Salin Doa"}
                </button>
              </div>
            </div>
          </div>
        )}

        {/* ════════════════════ QURAN ════════════════════ */}
        {tab==="quran" && (
          <div className="scr fi" style={{padding:'0 16px 20px'}}>
            <div style={{padding:'14px 0 12px'}}>
              <h2 style={{margin:0,color:T.text,fontSize:21,fontWeight:700}}>Al-Qur'an</h2>
              <p style={{margin:'3px 0 0',color:T.textMute,fontSize:12}}>Tilawah harian Ramadhan</p>
            </div>
            <div style={{borderRadius:20,padding:'15px',background:T.blueBg,border:`1px solid ${T.blueB}`,marginBottom:14}}>
              <p style={{margin:'0 0 8px',color:T.textSub,fontSize:12}}>Target Khatam Ramadhan</p>
              <div style={{display:'flex',justifyContent:'space-between',marginBottom:7}}>
                <span style={{color:T.text,fontSize:13,fontWeight:600}}>{ramDay?`Hari ${ramDay}`:"Belum Dimulai"} — Juz {ramDay||0}/30</span>
                <span style={{color:isDark?'#93c5fd':'#2563eb',fontSize:12,fontWeight:700}}>{ramDay?Math.round((ramDay/30)*100):0}%</span>
              </div>
              <div className="bar"><div className="bar-fill" style={{width:`${ramDay?Math.round((ramDay/30)*100):0}%`}}/></div>
            </div>
            {SURAH_LIST.map(s=>(
              <div key={s.no} style={{display:'flex',alignItems:'center',padding:'13px 14px',borderRadius:15,marginBottom:7,background:T.card,border:`1px solid ${T.cardB}`}}>
                <div style={{width:36,height:36,borderRadius:9,background:T.accent,border:`1px solid ${T.accentB}`,display:'flex',alignItems:'center',justifyContent:'center',marginRight:12,flexShrink:0}}>
                  <span style={{color:T.gold,fontSize:11,fontWeight:700}}>{s.no}</span>
                </div>
                <div style={{flex:1}}>
                  <p style={{margin:0,color:T.text,fontSize:13,fontWeight:500}}>{s.name}</p>
                  <p style={{margin:'1px 0 0',color:T.textMute,fontSize:11}}>{s.ayat} Ayat · Juz {s.juz}</p>
                </div>
                <p className="arabic" style={{margin:0,color:T.goldDim,fontSize:15}}>{s.ar}</p>
              </div>
            ))}
            <div style={{textAlign:'center',padding:'14px',color:T.textMute,fontSize:12}}>Untuk membaca lengkap, gunakan aplikasi Al-Qur'an terpisah 📖</div>
          </div>
        )}

        {/* ─── Bottom Nav ─── */}
        <nav className="bnav">
          <div style={{display:'flex',justifyContent:'space-around'}}>
            {[{id:"home",icon:"🏠",label:"Beranda"},{id:"jadwal",icon:"🕌",label:"Jadwal"},{id:"kajian",icon:"📚",label:"Kajian"},{id:"doa",icon:"🤲",label:"Doa"},{id:"quran",icon:"📖",label:"Qur'an"}]
              .map(t=>(
              <button key={t.id} onClick={()=>{setTab(t.id);setSelKajian(null);setSelDoa(null);}} style={{background:'none',border:'none',cursor:'pointer',display:'flex',flexDirection:'column',alignItems:'center',gap:2,padding:'4px 12px'}}>
                <span style={{fontSize:20,transition:'transform 0.2s',display:'block',transform:tab===t.id?'scale(1.14)':'scale(1)'}}>{t.icon}</span>
                <span style={{fontSize:10,fontWeight:tab===t.id?700:400,color:tab===t.id?T.gold:T.textMute,fontFamily:'Outfit,sans-serif'}}>{t.label}</span>
                {tab===t.id && <div style={{width:4,height:4,borderRadius:'50%',background:T.gold}}/>}
              </button>
            ))}
          </div>
        </nav>

        {/* ════════════════════ LOCATION MODAL ════════════════════ */}
        {showLoc && (
          <div className="moverlay" onClick={()=>setShowLoc(false)}>
            <div className="msheet" onClick={e=>e.stopPropagation()}>
              {/* Drag handle */}
              <div style={{display:'flex',justifyContent:'center',padding:'12px 0 4px'}}>
                <div style={{width:38,height:4,borderRadius:2,background:isDark?'rgba(255,255,255,0.18)':'rgba(0,0,0,0.14)'}}/>
              </div>
              {/* Header */}
              <div style={{padding:'8px 20px 13px',borderBottom:`1px solid ${T.div}`,display:'flex',justifyContent:'space-between',alignItems:'center'}}>
                <div>
                  <h3 style={{margin:0,color:T.text,fontSize:17,fontWeight:700}}>Pilih Wilayah</h3>
                  <p style={{margin:'3px 0 0',color:T.textMute,fontSize:11}}>📍 Saat ini: <strong style={{color:T.gold}}>{loc.name}</strong></p>
                </div>
                <button onClick={()=>setShowLoc(false)} style={{background:isDark?'rgba(255,255,255,0.07)':'rgba(0,0,0,0.06)',border:'none',borderRadius:10,width:30,height:30,cursor:'pointer',color:T.textSub,fontSize:14,display:'flex',alignItems:'center',justifyContent:'center'}}>✕</button>
              </div>
              {/* Search */}
              <div style={{padding:'12px 16px 8px'}}>
                <div style={{position:'relative'}}>
                  <span style={{position:'absolute',left:12,top:'50%',transform:'translateY(-50%)',fontSize:14,pointerEvents:'none'}}>🔍</span>
                  <input value={locQ} onChange={e=>setLocQ(e.target.value)} placeholder="Cari kota atau provinsi..." style={{width:'100%',background:T.input,border:`1px solid ${T.inputB}`,borderRadius:13,padding:'11px 12px 11px 36px',color:T.text,fontSize:14}}/>
                </div>
              </div>
              {/* City list */}
              <div style={{flex:1,overflow:'auto',paddingBottom:28}}>
                {locQ.trim() ? (
                  filtered.length===0
                    ? <div style={{textAlign:'center',padding:'30px',color:T.textMute,fontSize:13}}>Kota tidak ditemukan 🔍</div>
                    : filtered.map(city=>(
                      <div key={city.name} className="provrow" onClick={()=>{setLoc(city);setShowLoc(false);setLocQ("");}} style={{display:'flex',justifyContent:'space-between',alignItems:'center',padding:'13px 20px',borderBottom:`1px solid ${T.div}`,background:'transparent'}}>
                        <div>
                          <p style={{margin:0,color:loc.name===city.name?T.gold:T.text,fontSize:14,fontWeight:loc.name===city.name?600:400}}>{city.name}</p>
                          <p style={{margin:'2px 0 0',color:T.textMute,fontSize:11}}>{city.province} · WIB{city.tz>7?`+${city.tz-7}`:''}</p>
                        </div>
                        {loc.name===city.name && <span style={{color:T.gold,fontSize:16}}>✓</span>}
                      </div>
                    ))
                ) : (
                  CITIES.map(prov=>(
                    <div key={prov.province}>
                      <div className="provrow" onClick={()=>setExpProv(expProv===prov.province?null:prov.province)} style={{display:'flex',justifyContent:'space-between',alignItems:'center',padding:'12px 20px',borderBottom:`1px solid ${T.div}`,background:expProv===prov.province?T.provActive:'transparent'}}>
                        <div style={{display:'flex',alignItems:'center',gap:8}}>
                          <span style={{color:T.text,fontSize:13,fontWeight:600}}>{prov.province}</span>
                          {prov.cities.some(c=>c.name===loc.name) && <span style={{background:T.accent,border:`1px solid ${T.accentB}`,borderRadius:6,padding:'1px 7px',color:T.gold,fontSize:9,fontWeight:700}}>AKTIF</span>}
                        </div>
                        <div style={{display:'flex',alignItems:'center',gap:6}}>
                          <span style={{color:T.textMute,fontSize:11}}>{prov.cities.length} kota</span>
                          <span style={{color:T.textMute,fontSize:13,transition:'transform 0.2s',display:'inline-block',transform:expProv===prov.province?'rotate(90deg)':'rotate(0deg)'}}>›</span>
                        </div>
                      </div>
                      {expProv===prov.province && prov.cities.map(city=>(
                        <div key={city.name} className="provrow" onClick={()=>{setLoc(city);setShowLoc(false);setLocQ("");setExpProv(null);}} style={{display:'flex',justifyContent:'space-between',alignItems:'center',padding:'11px 20px 11px 32px',background:isDark?'rgba(255,255,255,0.025)':'rgba(0,0,0,0.025)',borderBottom:`1px solid ${T.div}`}}>
                          <div>
                            <p style={{margin:0,color:loc.name===city.name?T.gold:T.text,fontSize:13,fontWeight:loc.name===city.name?600:400}}>{city.name}</p>
                            <p style={{margin:'2px 0 0',color:T.textMute,fontSize:10}}>Zona WIB{city.tz>7?`+${city.tz-7}`:''}</p>
                          </div>
                          {loc.name===city.name && <span style={{color:T.gold,fontSize:15}}>✓</span>}
                        </div>
                      ))}
                    </div>
                  ))
                )}
              </div>
            </div>
          </div>
        )}
      </div>
    </>
  );
}
