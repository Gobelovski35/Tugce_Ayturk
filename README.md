<!DOCTYPE html>
<html lang="tr">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>Sanatçı Portföy</title>
<style>
*{box-sizing:border-box;margin:0;padding:0;}
body{font-family:-apple-system,BlinkMacSystemFont,"Segoe UI",sans-serif;background:#f7f5f2;color:#1a1a1a;font-size:14px;line-height:1.5;}
a{color:inherit;text-decoration:none;}

/* HEADER */
.header{background:#fff;border-bottom:1px solid #e8e4de;padding:20px 24px;display:flex;align-items:center;gap:16px;position:sticky;top:0;z-index:50;}
.avatar{width:52px;height:52px;border-radius:50%;background:#FAECE7;color:#D85A30;display:flex;align-items:center;justify-content:center;font-size:20px;font-weight:500;flex-shrink:0;}
.hname{font-size:17px;font-weight:600;color:#1a1a1a;}
.hsub{font-size:12px;color:#888;margin-top:2px;}
.hstats{display:flex;gap:16px;margin-top:5px;}
.hstat{font-size:11px;color:#aaa;}<br>.hstat strong{color:#555;font-weight:600;}

/* NAV */
.nav{display:flex;gap:6px;flex-wrap:wrap;padding:14px 24px 12px;background:#fff;border-bottom:1px solid #e8e4de;position:sticky;top:81px;z-index:40;}
.nb{display:flex;align-items:center;gap:5px;padding:6px 14px;border-radius:20px;border:1px solid #e0ddd8;background:transparent;font-size:12px;color:#777;cursor:pointer;transition:all .15s;white-space:nowrap;}
.nb .dot{width:7px;height:7px;border-radius:50%;flex-shrink:0;}
.nb.active{color:#fff;border-color:transparent;}
.nb:hover:not(.active){background:#f0ede8;}

/* SECTION */
.sec-hdr{padding:18px 24px 8px;display:flex;align-items:center;justify-content:space-between;}
.sec-ttl{font-size:11px;font-weight:600;color:#aaa;letter-spacing:.06em;text-transform:uppercase;}
.sec-cnt{font-size:11px;color:#bbb;}

/* LIST */
.list{padding:0 24px 32px;display:flex;flex-direction:column;gap:2px;}
.item{background:#fff;border:1px solid #ece9e4;border-radius:10px;overflow:hidden;transition:border-color .15s;}
.item:hover{border-color:#ccc;}
.item.open{border-color:#ccc;}
.item-row{display:flex;align-items:center;gap:12px;padding:13px 16px;cursor:pointer;user-select:none;}
.idot{width:9px;height:9px;border-radius:50%;flex-shrink:0;}
.iyear{font-size:11px;color:#bbb;min-width:46px;flex-shrink:0;}
.icontent{flex:1;min-width:0;}
.ititle{font-size:13px;font-weight:500;color:#1a1a1a;line-height:1.35;}
.isub{font-size:11px;color:#999;margin-top:2px;}
.iright{display:flex;align-items:center;gap:8px;flex-shrink:0;}
.itag{font-size:10px;padding:2px 9px;border-radius:10px;font-weight:500;white-space:nowrap;}
.iloc{font-size:10px;color:#bbb;max-width:70px;text-align:right;display:none;}
.ichev{font-size:16px;color:#ccc;transition:transform .2s;flex-shrink:0;}
.item.open .ichev{transform:rotate(180deg);}

/* EXPAND */
.expand{display:none;border-top:1px solid #f0ede8;padding:14px 16px 16px;background:#faf8f6;}
.item.open .expand{display:block;}
.exp-desc{font-size:12.5px;color:#666;line-height:1.6;margin-bottom:14px;}
.exp-meta{display:grid;grid-template-columns:repeat(3,1fr);gap:8px;margin-bottom:14px;}
.mbox{background:#fff;border:1px solid #ece9e4;border-radius:8px;padding:8px 10px;}
.mlbl{font-size:9px;color:#bbb;text-transform:uppercase;letter-spacing:.05em;margin-bottom:3px;}
.mval{font-size:12px;font-weight:500;color:#333;}
.gallery-ttl{font-size:11px;font-weight:600;color:#bbb;letter-spacing:.05em;text-transform:uppercase;margin-bottom:8px;}
.gallery{display:flex;gap:8px;flex-wrap:wrap;}
.gimg{width:calc(33.33% - 6px);aspect-ratio:4/3;border-radius:8px;overflow:hidden;cursor:pointer;border:1px solid #ece9e4;transition:transform .12s,border-color .12s;position:relative;background:#f0ede8;display:flex;align-items:center;justify-content:center;flex-direction:column;gap:4px;}
.gimg:hover{transform:scale(1.02);border-color:#ccc;}
.gimg img{width:100%;height:100%;object-fit:cover;position:absolute;inset:0;}
.gimg-lbl{font-size:9px;color:rgba(0,0,0,.3);position:relative;z-index:1;}
.gimg-em{font-size:22px;opacity:.45;position:relative;z-index:1;}
.add-btn{margin-top:10px;display:inline-flex;align-items:center;gap:5px;font-size:11px;color:#aaa;border:1px dashed #ddd;border-radius:8px;padding:7px 13px;cursor:pointer;background:transparent;transition:all .15s;width:100%;justify-content:center;}
.add-btn:hover{background:#f0ede8;border-color:#ccc;color:#777;}

/* LIGHTBOX */
.lb{position:fixed;inset:0;background:rgba(0,0,0,.88);display:none;align-items:center;justify-content:center;z-index:200;padding:20px;}
.lb.open{display:flex;}
.lbbox{background:#fff;border-radius:14px;width:min(580px,100%);max-height:88vh;overflow-y:auto;}
.lbhead{display:flex;align-items:center;gap:10px;padding:14px 16px;border-bottom:1px solid #ece9e4;position:sticky;top:0;background:#fff;z-index:1;}
.lbicon{width:36px;height:36px;border-radius:50%;display:flex;align-items:center;justify-content:center;font-size:15px;flex-shrink:0;}
.lbt{font-size:13px;font-weight:600;}
.lbs{font-size:11px;color:#999;margin-top:1px;}
.lbclose{margin-left:auto;background:none;border:none;font-size:22px;cursor:pointer;color:#bbb;line-height:1;padding:2px 6px;}
.lbbody{padding:14px 16px 18px;}
.lbfull{width:100%;aspect-ratio:16/9;border-radius:10px;overflow:hidden;margin-bottom:8px;border:1px solid #ece9e4;background:#f0ede8;display:flex;align-items:center;justify-content:center;flex-direction:column;gap:8px;}
.lbfull img{width:100%;height:100%;object-fit:cover;}
.lbcap{font-size:11px;color:#bbb;text-align:center;margin-bottom:12px;}
.lbthumbs{display:flex;gap:8px;margin-bottom:14px;}
.lbth{flex:1;aspect-ratio:1;border-radius:8px;overflow:hidden;cursor:pointer;border:2px solid transparent;transition:border-color .12s;background:#f0ede8;display:flex;align-items:center;justify-content:center;flex-direction:column;gap:3px;}
.lbth.active{border-color:#D85A30;}
.lbth:hover:not(.active){border-color:#ccc;}
.lbth img{width:100%;height:100%;object-fit:cover;}
.lbmetag{display:grid;grid-template-columns:1fr 1fr;gap:8px;margin-bottom:12px;}
.lbmb{padding:9px 11px;border-radius:9px;background:#faf8f6;border:1px solid #ece9e4;}
.lbml{font-size:9px;color:#bbb;text-transform:uppercase;letter-spacing:.05em;margin-bottom:3px;}
.lbmv{font-size:12px;font-weight:500;color:#333;}
.lbdesc{font-size:12.5px;color:#666;line-height:1.6;padding:11px 13px;border-radius:9px;background:#faf8f6;border:1px solid #ece9e4;}

/* UPLOAD AREA */
.upload-area{border:2px dashed #e0ddd8;border-radius:10px;padding:20px;text-align:center;cursor:pointer;transition:all .15s;margin-bottom:14px;}
.upload-area:hover{border-color:#aaa;background:#faf8f6;}
.upload-area p{font-size:12px;color:#bbb;margin-top:6px;}

@media(max-width:520px){
  .header{padding:14px 16px;}
  .nav{padding:10px 16px;top:78px;}
  .sec-hdr,.list{padding-left:16px;padding-right:16px;}
  .exp-meta{grid-template-columns:1fr 1fr;}
  .lbmetag{grid-template-columns:1fr;}
  .gimg{width:calc(50% - 4px);}
}
</style>
</head>
<body>

<div class="header">
  <div class="avatar">H</div>
  <div>
    <div class="hname">Heykeltıraş</div>
    <div class="hsub">Dokuz Eylül Üniversitesi · Güzel Sanatlar Fakültesi</div>
    <div class="hstats">
      <span class="hstat"><strong>49</strong> etkinlik</span>
      <span class="hstat"><strong>12</strong> ülke</span>
      <span class="hstat"><strong>2013–2025</strong></span>
    </div>
  </div>
</div>

<div class="nav" id="nav"></div>
<div class="sec-hdr"><span class="sec-ttl" id="sec-ttl">Tüm Etkinlikler</span><span class="sec-cnt" id="sec-cnt"></span></div>
<div class="list" id="list"></div>

<!-- LIGHTBOX -->
<div class="lb" id="lb" onclick="lbBg(event)">
  <div class="lbbox">
    <div class="lbhead">
      <div class="lbicon" id="lb-icon"></div>
      <div><div class="lbt" id="lb-title"></div><div class="lbs" id="lb-sub"></div></div>
      <button class="lbclose" onclick="closeLb()">✕</button>
    </div>
    <div class="lbbody">
      <div class="lbfull" id="lb-full"></div>
      <div class="lbcap" id="lb-cap"></div>
      <div class="lbthumbs" id="lb-thumbs"></div>
      <div class="lbmetag" id="lb-meta"></div>
      <div class="lbdesc" id="lb-desc"></div>
    </div>
  </div>
</div>

<script>
const CATS={
  sergi: {name:"Sergi",    color:"#7F77DD",light:"#EEEDFE",dark:"#3C3489",icon:"🖼️"},
  semp:  {name:"Sempozyum",color:"#1D9E75",light:"#E1F5EE",dark:"#085041",icon:"🌿"},
  yayin: {name:"Yayın",    color:"#BA7517",light:"#FAEEDA",dark:"#633806",icon:"📄"},
  odul:  {name:"Ödül",     color:"#D4537E",light:"#FBEAF0",dark:"#72243E",icon:"🏆"},
  egitim:{name:"Eğitim",   color:"#888780",light:"#F1EFE8",dark:"#444441",icon:"🎓"},
};

const GRADS={
  sergi: [["#ede9fc","#c4bff5","🗿"],["#e8e4fc","#a09aed","🧱"],["#f2f0fe","#b8b3f0","⬜"]],
  semp:  [["#e0f5ed","#9fddc5","🌲"],["#d4f0e6","#5dcaa5","🍃"],["#e8f8f2","#afe0c8","🌿"]],
  yayin: [["#faeeda","#f5c97a","📰"],["#fdf3e3","#eaab4a","✏️"],["#fff8ee","#e09920","📖"]],
  odul:  [["#fbeaf0","#ed93b1","🏅"],["#f8e0ea","#d4537e","🎖️"],["#fce8f0","#c04878","⭐"]],
  egitim:[["#f1efe8","#c0bdb5","🏛️"],["#eceae3","#aaa79f","📚"],["#e8e6de","#98958e","🎨"]],
};

// Per-item uploaded images storage
const uploadedImages = {};

const DATA=[
  {id:"e1",cat:"egitim",year:"2008–14",title:"DEÜ Güzel Sanatlar — Heykel Bölümü",detail:"Lisans · İzmir · Not: 73.23",loc:"İzmir",desc:"Dokuz Eylül Üniversitesi Güzel Sanatlar Fakültesi Heykel Bölümü'nden 73.23 not ortalamasıyla mezuniyet. Dört yıl boyunca taş, mermer, bronz ve ahşap gibi geleneksel heykel malzemeleriyle çalışıldı.",imgs:[{lbl:"Atölye ortamı"},{lbl:"Mezuniyet sergisi"},{lbl:"Fakülte binası"}]},
  {id:"e2",cat:"egitim",year:"2015–19",title:"DEÜ Sanat ve Tasarım Yüksek Lisans",detail:"Master · İzmir · GPA: 3.96",loc:"İzmir",desc:"DEÜ Güzel Sanatlar Enstitüsü'nde Sanat ve Tasarım alanında yüksek lisans. Tez çalışması doğa sanatı ve malzeme üzerine yoğunlaşmıştır.",imgs:[{lbl:"Tez çalışması"},{lbl:"Stüdyo"},{lbl:"Sergi açılışı"}]},
  {id:"o1",cat:"odul",year:2013,title:"12. EÇEV Heykel Yarışması",detail:"Mansiyon Ödülü",loc:"Türkiye",desc:"EÇEV tarafından düzenlenen ulusal heykel yarışmasında mansiyon ödülü.",imgs:[{lbl:"Ödül töreni"},{lbl:"Eser fotoğrafı"},{lbl:"Sergileme"}]},
  {id:"o2",cat:"odul",year:2014,title:"13. EÇEV Heykel Yarışması",detail:"Mansiyon Ödülü",loc:"Türkiye",desc:"Bir yıl arayla aynı yarışmada ikinci mansiyon ödülü.",imgs:[{lbl:"Yarışma eseri"},{lbl:"Sergi alanı"},{lbl:"Ödül belgesi"}]},
  {id:"o3",cat:"odul",year:2015,title:"Turgut Pura Heykel Yarışması",detail:"Kültür Bak. Ödülü · Ankara",loc:"Ankara",desc:"T.C. Kültür ve Turizm Bakanlığı Devlet Resim Heykel Müzesi Ödülü.",imgs:[{lbl:"Eser"},{lbl:"Müze sergileme"},{lbl:"Tören"}]},
  {id:"o4",cat:"odul",year:2016,title:"2. Genç Güncel Proje Yarışması",detail:"Mansiyon · Kültür Bakanlığı",loc:"Ankara",desc:"T.C. Kültür ve Turizm Bakanlığı Devlet Resim Heykel Müzesi tarafından verilen mansiyon.",imgs:[{lbl:"Proje görseli"},{lbl:"Jüri sunumu"},{lbl:"Sergi"}]},
  {id:"y1",cat:"yayin",year:2016,title:"'Yeni Anlam, Doğal Taş, Rodin ile Kazanıldı'",detail:"Tr Stone Magazine · Kasım–Aralık",loc:"Türkiye",desc:"Doğal taş heykelinde anlam ve Rodin'in mirası üzerine analitik bir değerlendirme.",imgs:[{lbl:"Dergi kapağı"},{lbl:"Makale sayfası"},{lbl:"Rodin eseri"}]},
  {id:"y2",cat:"yayin",year:2017,title:"'Brancusi ve Heykele Ait Kaidesi'",detail:"Tr Stone Magazine · Ocak–Şubat",loc:"Türkiye",desc:"Brancusi'nin kaide anlayışının heykel pratiğindeki dönüştürücü etkisi üzerine.",imgs:[{lbl:"Dergi"},{lbl:"Brancusi eseri"},{lbl:"Makale"}]},
  {id:"y3",cat:"yayin",year:2017,title:"'Donald Judd ve Soyut Heykelde Renk'",detail:"Tr Stone Magazine · Mart–Nisan",loc:"Türkiye",desc:"Minimalist heykelci Judd'ın renk kullanımının soyut heykel bağlamında incelenmesi.",imgs:[{lbl:"Makale"},{lbl:"Judd eseri"},{lbl:"Renk analizi"}]},
  {id:"y4",cat:"yayin",year:2018,title:"'Bir İfade Sanatı; Heykel'",detail:"Tr Stone Magazine · Temmuz–Ağustos",loc:"Türkiye",desc:"Heykel sanatının ifade biçimleri üzerine kapsamlı bir değerlendirme.",imgs:[{lbl:"Dergi"},{lbl:"Eser fotoğrafı"},{lbl:"Stüdyo"}]},
  {id:"y5",cat:"yayin",year:2018,title:"'Doğa Sanatı ve Doğal Taş'",detail:"Tr Stone Magazine · Eylül–Ekim",loc:"Türkiye",desc:"Doğa sanatı pratiğinde doğal taş kullanımının estetik ve ekolojik boyutları.",imgs:[{lbl:"Makale"},{lbl:"Doğa çalışması"},{lbl:"Taş malzeme"}]},
  {id:"y6",cat:"yayin",year:2018,title:"'Büyük Efes Art, Dinamo3 Sergisi'",detail:"Tr Stone Magazine · Kasım–Aralık",loc:"Türkiye",desc:"Büyük Efes Sanat Günleri Dinamo3 sergisinin eleştirel değerlendirmesi.",imgs:[{lbl:"Sergi görseli"},{lbl:"Dergi"},{lbl:"Eser"}]},
  {id:"y7",cat:"yayin",year:2019,title:"'Sanat Piyasası ve Çağdaş Sanat'",detail:"Tr Stone Magazine · Mart–Nisan",loc:"Türkiye",desc:"Günümüz sanat piyasasının dinamikleri ve çağdaş sanat üretimi üzerine bir bakış.",imgs:[{lbl:"Makale"},{lbl:"Sergi"},{lbl:"Piyasa görseli"}]},
  {id:"s1",cat:"sergi",year:2013,title:"'Identity' — Solo Sergi",detail:"Özdemir Nutku Tiyatroları · İzmir",loc:"İzmir",solo:true,desc:"İlk kişisel sergisi. Kimlik kavramını heykel diliyle araştıran kapsamlı bir sunum. Özdemir Nutku Tiyatroları Fuayesi'nde gerçekleşti.",imgs:[{lbl:"Sergi genel"},{lbl:"Eser detayı"},{lbl:"Açılış"}]},
  {id:"s2",cat:"sergi",year:2013,title:"EgeArt 5. Uluslararası Sergi",detail:"Ege Üniversitesi · İzmir",loc:"İzmir",desc:"Ege Üniversitesi'nin uluslararası çağdaş sanat sergisine katılım.",imgs:[{lbl:"Sergi alanı"},{lbl:"Eser"},{lbl:"Katılımcılar"}]},
  {id:"s3",cat:"sergi",year:2014,title:"Siemens Art — 'Sınırlar Yörüngeler'",detail:"DepoArt · İstanbul",loc:"İstanbul",desc:"Siemens Art sponsorluğunda DepoArt'ta gerçekleşen çağdaş sanat etkinliği.",imgs:[{lbl:"Mekan"},{lbl:"Eser"},{lbl:"Açılış"}]},
  {id:"s4",cat:"sergi",year:2015,title:"Od'A — Ouvroir d'Art",detail:"Türkiye'den Çağdaş Sanatçılar · İstanbul",loc:"İstanbul",desc:"Türkiye'den yeni nesil sanatçıları uluslararası platforma taşıyan seçkili sergi.",imgs:[{lbl:"Sergi"},{lbl:"Eser detayı"},{lbl:"Mekan"}]},
  {id:"s5",cat:"sergi",year:2015,title:"Ahmed Adnan Saygun Sanat Merkezi",detail:"Dünya Sanat Günleri · İzmir",loc:"İzmir",desc:"Ahmed Adnan Saygun Sanat Merkezi'nde düzenlenen Dünya Sanat Günleri etkinliği.",imgs:[{lbl:"Merkez"},{lbl:"Eser"},{lbl:"Etkinlik"}]},
  {id:"s6",cat:"sergi",year:2016,title:"Büyük Efes Sanat Günleri",detail:"Swissotel · İzmir",loc:"İzmir",desc:"Swissotel İzmir'de düzenlenen Büyük Efes Sanat Günleri karma sergisi.",imgs:[{lbl:"Swissotel"},{lbl:"Eser"},{lbl:"Sergi"}]},
  {id:"s7",cat:"sergi",year:2016,title:"Swissotel Dinamo2",detail:"İzmir",loc:"İzmir",desc:"Swissotel İzmir'de gerçekleşen Dinamo serisinin ikinci bölümü.",imgs:[{lbl:"Mekan"},{lbl:"Eser"},{lbl:"Açılış"}]},
  {id:"s8",cat:"sergi",year:2016,title:"'Kaçak Gölge' Sergisi",detail:"Elgiz Müzesi · İstanbul",loc:"İstanbul",desc:"Elgiz Müzesi'nin prestijli sergi programında yer alan grup sergisi.",imgs:[{lbl:"Müze"},{lbl:"Eser"},{lbl:"Sergi alanı"}]},
  {id:"s9",cat:"sergi",year:2016,title:"'Sığla Ormanında Sanat'",detail:"Londra · Ankara · Bodrum · Marmaris",loc:"Çok Mekanlı",desc:"Dört farklı şehirde eş zamanlı gerçekleşen doğa odaklı sergi projesi.",imgs:[{lbl:"Londra"},{lbl:"Doğa çalışması"},{lbl:"Bodrum"}]},
  {id:"s10",cat:"sergi",year:2017,title:"GNAP Rural Stage",detail:"Bulgaristan · Romanya · Macaristan",loc:"Balkanlar",desc:"Global Nomadic Art Project'in kırsal alanları kapsayan Doğu Avrupa ayağı.",imgs:[{lbl:"Doğu Avrupa"},{lbl:"Doğa"},{lbl:"Grup çalışma"}]},
  {id:"s11",cat:"sergi",year:2017,title:"GNAP — Doğanın İzinde",detail:"Türkiye",loc:"Türkiye",desc:"Türkiye'de gerçekleşen GNAP etkinliği. Doğa ve sanat üretimi odaklı.",imgs:[{lbl:"Türkiye doğa"},{lbl:"Çalışma"},{lbl:"Eser"}]},
  {id:"s12",cat:"sergi",year:2017,title:"Gaziantep Üniversitesi Doğa Sanatı",detail:"Gaziantep",loc:"Gaziantep",desc:"Gaziantep Üniversitesi bünyesinde düzenlenen doğa sanatı grup sergisi.",imgs:[{lbl:"Mekan"},{lbl:"Eser"},{lbl:"Sergi"}]},
  {id:"s13",cat:"sergi",year:2017,title:"DEÜ Heykel Bölümü 30 Yıl",detail:"Dokuz Eylül Üniversitesi · İzmir",loc:"İzmir",desc:"Heykel bölümünün 30. yılına özel düzenlenen retrospektif grup sergisi.",imgs:[{lbl:"Fakülte sergisi"},{lbl:"Eserler"},{lbl:"Açılış"}]},
  {id:"s14",cat:"sergi",year:2018,title:"Doğa Sanatı Sergisi",detail:"Güney Kore",loc:"Güney Kore",desc:"Kore'de düzenlenen uluslararası doğa sanatı seçkisine katılım.",imgs:[{lbl:"Kore mekanı"},{lbl:"Eser"},{lbl:"Doğa"}]},
  {id:"s15",cat:"sergi",year:2018,title:"12×12×12 Cube",detail:"Güney Kore",loc:"Güney Kore",desc:"12×12×12 cm küp formatında eserlerin sergilendiği uluslararası proje.",imgs:[{lbl:"Küp sergi"},{lbl:"Eser"},{lbl:"Mekan"}]},
  {id:"s16",cat:"sergi",year:2018,title:"PortİZMİR 4 — Breathe",detail:"İzmir",loc:"İzmir",desc:"Nefes alma temalı kentsel sanat projesine katılım.",imgs:[{lbl:"Liman alanı"},{lbl:"Eser"},{lbl:"Açılış"}]},
  {id:"s17",cat:"sergi",year:2018,title:"Coleoptera",detail:"Ankara",loc:"Ankara",desc:"Böcek biyolojisinden esinlenen tematik çağdaş sanat sergisi.",imgs:[{lbl:"Sergi"},{lbl:"Eser"},{lbl:"Detay"}]},
  {id:"s18",cat:"sergi",year:2018,title:"Dinamo 3",detail:"Swissotel · İzmir",loc:"İzmir",desc:"Swissotel İzmir'de devam eden Dinamo serisinin üçüncü bölümü.",imgs:[{lbl:"Mekan"},{lbl:"Eser"},{lbl:"Sergi"}]},
  {id:"s19",cat:"sergi",year:2019,title:"Swissotel Büyükefes Sanat Günleri",detail:"İzmir",loc:"İzmir",desc:"Swissotel İzmir ev sahipliğinde düzenlenen Büyükefes Sanat Günleri.",imgs:[{lbl:"Swissotel"},{lbl:"Eser"},{lbl:"Sergi"}]},
  {id:"s20",cat:"sergi",year:2019,title:"Down to Earth",detail:"Muğla · Bodrum",loc:"Muğla",desc:"Toprak ve doğa ile ilişkiyi araştıran iki mekanlı proje.",imgs:[{lbl:"Doğa alanı"},{lbl:"Eser"},{lbl:"Bodrum"}]},
  {id:"s21",cat:"sergi",year:2019,title:"EgeArt 8. Uluslararası Sergi",detail:"Ege Üniversitesi · İzmir",loc:"İzmir",desc:"İzmir'in köklü uluslararası sanat etkinliğine ikinci katılım.",imgs:[{lbl:"Sergi alanı"},{lbl:"Eser"},{lbl:"Açılış"}]},
  {id:"s22",cat:"sergi",year:2019,title:"KUAKMER Doğa Sanatı",detail:"İzmir · Kuşadası",loc:"İzmir",desc:"Kuşadası'nda gerçekleşen doğa sanatı etkinliği.",imgs:[{lbl:"Doğa"},{lbl:"Eser"},{lbl:"Kuşadası"}]},
  {id:"s23",cat:"sergi",year:2019,title:"12×12×12 Cube (2)",detail:"Güney Kore",loc:"Güney Kore",desc:"12×12×12 Cube projesinin ikinci yılına katılım.",imgs:[{lbl:"Kore"},{lbl:"Küp eser"},{lbl:"Mekan"}]},
  {id:"s24",cat:"sergi",year:2021,title:"Natureart Exhibition",detail:"Güney Kore",loc:"Güney Kore",desc:"Kore'de düzenlenen Natureart uluslararası doğa sanatı sergisi.",imgs:[{lbl:"Kore doğa"},{lbl:"Proje"},{lbl:"Eser"}]},
  {id:"s25",cat:"sergi",year:2022,title:"'Farazi'",detail:"İstanbul",loc:"İstanbul",desc:"Kavramsal heykel çalışmalarını içeren güncel sergi.",imgs:[{lbl:"Mekan"},{lbl:"Eser"},{lbl:"Detay"}]},
  {id:"s26",cat:"sergi",year:2022,title:"QNB Finans — 'Kırılma Noktası'",detail:"İstanbul",loc:"İstanbul",desc:"Finans ve sanat kesişiminde düzenlenen kurumsal sergi.",imgs:[{lbl:"QNB mekanı"},{lbl:"Eser"},{lbl:"Sergi"}]},
  {id:"s27",cat:"sergi",year:2022,title:"Raffles İstanbul — 'Sofralar'",detail:"Lobi · İstanbul",loc:"İstanbul",desc:"Raffles İstanbul lobisinde sergilenen özel üretim eser.",imgs:[{lbl:"Raffles lobi"},{lbl:"Eser"},{lbl:"Kurulum"}]},
  {id:"s28",cat:"sergi",year:2024,title:"Itsliquid Contemporary Art Fair",detail:"Roma · İtalya",loc:"Roma",desc:"Roma'da düzenlenen uluslararası çağdaş sanat fuarına katılım.",imgs:[{lbl:"Roma fuarı"},{lbl:"Stand"},{lbl:"Eser"}]},
  {id:"s29",cat:"sergi",year:2025,title:"Global Nomadic Art Project",detail:"Güney Kore",loc:"Güney Kore",desc:"Göçebe sanat anlayışını dünya genelinde yaşatan uzun soluklu projenin Kore ayağı.",imgs:[{lbl:"Kore doğa"},{lbl:"Proje"},{lbl:"Eser"}]},
  {id:"p1",cat:"semp",year:2016,title:"Doğa Sanatı Kış Atölyesi",detail:"YATOO Projesi · İzmir",loc:"İzmir",desc:"YATOO International'ın kış doğa sanatı atölye programına katılım.",imgs:[{lbl:"Atölye"},{lbl:"Doğa çalışması"},{lbl:"Grup"}]},
  {id:"p2",cat:"semp",year:2016,title:"Dünya Sanat Günü Çizim Atölyesi",detail:"Kültür Bakanlığı · İzmir",loc:"İzmir",desc:"T.C. Kültür Bakanlığı Devlet Resim Heykel Müzesi organizasyonu.",imgs:[{lbl:"Atölye"},{lbl:"Katılımcılar"},{lbl:"Müze"}]},
  {id:"p3",cat:"semp",year:2016,title:"'Doğada Sanat'",detail:"Doğayı Koruma Merkezi · Muğla",loc:"Muğla",desc:"Doğal alanda üretimi ön plana çıkaran açık hava sempozyumu.",imgs:[{lbl:"Muğla doğa"},{lbl:"Üretim süreci"},{lbl:"Eser"}]},
  {id:"p4",cat:"semp",year:2016,title:"Steinbildhauen — Arbeit am Stein",detail:"Almanya",loc:"Almanya",desc:"Almanya'da taş heykel odaklı uluslararası çalışma atölyesi.",imgs:[{lbl:"Almanya"},{lbl:"Taş işleme"},{lbl:"Sempozyum"}]},
  {id:"p5",cat:"semp",year:2017,title:"GNAP 2017 Doğu Avrupa",detail:"Macaristan · Romanya · Bulgaristan",loc:"Doğu Avrupa",desc:"Global Nomadic Art Project'in Doğu Avrupa rotasyonuna katılım.",imgs:[{lbl:"Macaristan"},{lbl:"Romanya"},{lbl:"Bulgaristan"}]},
  {id:"p6",cat:"semp",year:2017,title:"GNAP 2017 — Doğanın İzinde",detail:"Türkiye",loc:"Türkiye",desc:"Türkiye'de gerçekleşen GNAP etkinliği. Doğa ve sanat üretimi.",imgs:[{lbl:"Türkiye doğa"},{lbl:"Çalışma"},{lbl:"Eser"}]},
  {id:"p7",cat:"semp",year:2018,title:"Uluslararası Doğa Sanatı & Heykel Sempozyumu Gabrovtsi",detail:"Bulgaristan",loc:"Bulgaristan",desc:"Bulgaristan'ın Gabrovtsi köyünde düzenlenen uluslararası sempozyum.",imgs:[{lbl:"Gabrovtsi"},{lbl:"Doğa çalışması"},{lbl:"Sempozyum"}]},
  {id:"p8",cat:"semp",year:2022,title:"Gabrovtsi ART-NATURE — to-GET-here",detail:"Bulgaristan",loc:"Bulgaristan",desc:"Gabrovtsi sempozyumunun devamı niteliğinde uluslararası buluşma.",imgs:[{lbl:"Bulgaristan"},{lbl:"Üretim"},{lbl:"Katılımcılar"}]},
];

let currentCat="all";
let lbItem=null;
let lbImgIdx=0;

const NAVBTNS=[
  {cat:"all",label:"Tümü",color:"#D85A30"},
  {cat:"sergi",label:"Sergi",color:"#7F77DD"},
  {cat:"semp",label:"Sempozyum",color:"#1D9E75"},
  {cat:"yayin",label:"Yayın",color:"#BA7517"},
  {cat:"odul",label:"Ödül",color:"#D4537E"},
  {cat:"egitim",label:"Eğitim",color:"#888780"},
];

function buildNav(){
  document.getElementById('nav').innerHTML=NAVBTNS.map(b=>`
    <button class="nb${b.cat==='all'?' active':''}" data-cat="${b.cat}"
      style="${b.cat==='all'?`background:${b.color};border-color:${b.color};color:#fff;`:''}"
      onclick="setFilter('${b.cat}','${b.color}')">
      <span class="dot" style="background:${b.cat==='all'?'#fff':b.color};"></span>${b.label}
    </button>`).join('');
}

function setFilter(cat){
  currentCat=cat;
  document.querySelectorAll('.nb').forEach(b=>{
    const bc=b.dataset.cat;
    const info=NAVBTNS.find(x=>x.cat===bc);
    if(bc===cat){
      b.classList.add('active');
      b.style.background=info.color;b.style.borderColor=info.color;b.style.color='#fff';
      b.querySelector('.dot').style.background='#fff';
    } else {
      b.classList.remove('active');
      b.style.background='';b.style.borderColor='';b.style.color='';
      b.querySelector('.dot').style.background=info.color;
    }
  });
  renderList(cat);
}

function getItems(cat){
  return (cat==='all'?DATA:DATA.filter(d=>d.cat===cat)).sort((a,b)=>String(a.year).localeCompare(String(b.year)));
}

function thumbBg(cat,i){
  const g=GRADS[cat]||GRADS.sergi;
  const [c1,c2,em]=g[i%g.length];
  return {c1,c2,em};
}

function renderThumbHTML(item,i){
  const imgs=uploadedImages[item.id]||[];
  const src=imgs[i];
  const {c1,c2,em}=thumbBg(item.cat,i);
  if(src){
    return `<div class="gimg" onclick="event.stopPropagation();openLb(this.closest('.item').dataset.id,${i})"><img src="${src}" alt="${item.imgs[i].lbl}"><span class="gimg-lbl" style="position:absolute;bottom:4px;left:0;right:0;text-align:center;color:rgba(255,255,255,.7);font-size:9px;">${item.imgs[i].lbl}</span></div>`;
  }
  return `<div class="gimg" onclick="event.stopPropagation();triggerUpload('${item.id}',${i})" style="background:linear-gradient(135deg,${c1},${c2});">
    <span class="gimg-em">${em}</span>
    <span class="gimg-lbl">${item.imgs[i].lbl}</span>
  </div>`;
}

function renderList(cat){
  const items=getItems(cat);
  document.getElementById('sec-ttl').textContent=cat==='all'?'Tüm Etkinlikler':CATS[cat]?.name;
  document.getElementById('sec-cnt').textContent=items.length+' kayıt';
  document.getElementById('list').innerHTML=items.map(item=>{
    const c=CATS[item.cat];
    const solo=item.solo?`<span class="itag" style="background:${c.light};color:${c.dark};margin-left:4px;">Solo</span>`:'';
    return `<div class="item" data-id="${item.id}" id="item-${item.id}">
      <div class="item-row" onclick="toggleItem('${item.id}')">
        <div class="idot" style="background:${c.color};"></div>
        <div class="iyear">${item.year}</div>
        <div class="icontent">
          <div class="ititle">${item.title}</div>
          <div class="isub">${item.detail}</div>
        </div>
        <div class="iright">
          <span class="itag" style="background:${c.light};color:${c.dark};">${c.icon} ${c.name}</span>
          ${solo}
          <span class="iloc">${item.loc}</span>
          <span class="ichev">⌄</span>
        </div>
      </div>
      <div class="expand">
        <p class="exp-desc">${item.desc}</p>
        <div class="exp-meta">
          <div class="mbox"><div class="mlbl">Kategori</div><div class="mval" style="color:${c.color};">${c.name}</div></div>
          <div class="mbox"><div class="mlbl">Yıl</div><div class="mval">${item.year}</div></div>
          <div class="mbox"><div class="mlbl">Konum</div><div class="mval">${item.loc}</div></div>
        </div>
        <div class="gallery-ttl">Görseller</div>
        <div class="gallery" id="gal-${item.id}">
          ${item.imgs.map((_,i)=>renderThumbHTML(item,i)).join('')}
        </div>
        <label class="add-btn" onclick="event.stopPropagation();triggerUploadMulti('${item.id}')">
          + Görsel ekle
        </label>
        <input type="file" accept="image/*" multiple id="upl-${item.id}" style="display:none" onchange="handleUpload(event,'${item.id}')">
      </div>
    </div>`;
  }).join('');
}

function toggleItem(id){
  const el=document.getElementById('item-'+id);
  const wasOpen=el.classList.contains('open');
  document.querySelectorAll('.item.open').forEach(x=>x.classList.remove('open'));
  if(!wasOpen) el.classList.add('open');
}

function triggerUpload(id,idx){
  const input=document.getElementById('upl-'+id);
  input._targetIdx=idx;
  input.multiple=false;
  input.click();
}
function triggerUploadMulti(id){
  const input=document.getElementById('upl-'+id);
  input._targetIdx=null;
  input.multiple=true;
  input.click();
}

function handleUpload(e,id){
  const files=Array.from(e.target.files);
  const item=DATA.find(d=>d.id===id);
  if(!uploadedImages[id]) uploadedImages[id]=[];
  const idx=e.target._targetIdx;
  files.forEach((file,fi)=>{
    const reader=new FileReader();
    reader.onload=ev=>{
      const slot=idx!==null?idx:uploadedImages[id].length+fi;
      uploadedImages[id][slot]=ev.target.result;
      // re-render gallery
      const gal=document.getElementById('gal-'+id);
      if(gal) gal.innerHTML=item.imgs.map((_,i)=>renderThumbHTML(item,i)).join('');
    };
    reader.readAsDataURL(file);
  });
  e.target.value='';
}

function openLb(id,imgIdx){
  lbItem=DATA.find(d=>d.id===id);
  lbImgIdx=imgIdx||0;
  renderLb();
  document.getElementById('lb').classList.add('open');
}

function renderLb(){
  const item=lbItem;
  const c=CATS[item.cat];
  const imgs=uploadedImages[item.id]||[];
  document.getElementById('lb-icon').style.background=c.light;
  document.getElementById('lb-icon').textContent=c.icon;
  document.getElementById('lb-title').textContent=item.title;
  document.getElementById('lb-sub').innerHTML=`<span style="color:${c.color}">${c.name}</span> · ${item.year} · ${item.loc}`;

  const src=imgs[lbImgIdx];
  const {c1,c2,em}=thumbBg(item.cat,lbImgIdx);
  const full=document.getElementById('lb-full');
  if(src){
    full.innerHTML=`<img src="${src}" alt="${item.imgs[lbImgIdx].lbl}" style="width:100%;height:100%;object-fit:cover;">`;
  } else {
    full.innerHTML=`<div style="width:100%;height:100%;background:linear-gradient(135deg,${c1},${c2});display:flex;align-items:center;justify-content:center;flex-direction:column;gap:8px;">
      <span style="font-size:48px;opacity:.45;">${em}</span>
      <label style="font-size:12px;color:rgba(0,0,0,.35);cursor:pointer;" onclick="document.getElementById('lbupl-${item.id}').click()">Görsel yüklemek için tıklayın</label>
      <input type="file" accept="image/*" id="lbupl-${item.id}" style="display:none" onchange="handleLbUpload(event,'${item.id}',${lbImgIdx})">
    </div>`;
  }
  document.getElementById('lb-cap').textContent=item.imgs[lbImgIdx]?.lbl||'';

  document.getElementById('lb-thumbs').innerHTML=item.imgs.map((img,i)=>{
    const s=imgs[i];
    const {c1:tc1,c2:tc2,em:tem}=thumbBg(item.cat,i);
    return `<div class="lbth${i===lbImgIdx?' active':''}" onclick="lbImgIdx=${i};renderLb();">
      ${s?`<img src="${s}" alt="${img.lbl}">`:`<span style="font-size:16px;opacity:.45;">${tem}</span><span style="font-size:9px;color:rgba(0,0,0,.3);">${img.lbl}</span>`}
    </div>`;
  }).join('');

  document.getElementById('lb-meta').innerHTML=`
    <div class="lbmb"><div class="lbml">Kategori</div><div class="lbmv" style="color:${c.color};">${c.name}</div></div>
    <div class="lbmb"><div class="lbml">Yıl</div><div class="lbmv">${item.year}</div></div>
    <div class="lbmb" style="grid-column:1/-1"><div class="lbml">Konum</div><div class="lbmv">${item.loc}</div></div>`;
  document.getElementById('lb-desc').textContent=item.desc;
}

function handleLbUpload(e,id,idx){
  const file=e.target.files[0]; if(!file) return;
  const item=DATA.find(d=>d.id===id);
  if(!uploadedImages[id]) uploadedImages[id]=[];
  const reader=new FileReader();
  reader.onload=ev=>{
    uploadedImages[id][idx]=ev.target.result;
    // refresh gallery in list too
    const gal=document.getElementById('gal-'+id);
    if(gal) gal.innerHTML=item.imgs.map((_,i)=>renderThumbHTML(item,i)).join('');
    renderLb();
  };
  reader.readAsDataURL(file);
}

function closeLb(){document.getElementById('lb').classList.remove('open');}
function lbBg(e){if(e.target===document.getElementById('lb'))closeLb();}

buildNav();
renderList('all');
</script>
</body>
</html>
