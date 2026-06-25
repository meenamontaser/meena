<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>مينا للبرمجة</title>
<meta name="description" content="مشاريع برمجية، متجر إلكتروني، ودعم فني متكامل">
<link href="https://fonts.googleapis.com/css2?family=Cairo:wght@300;400;600;700;900&display=swap" rel="stylesheet">
<style>
:root{--gold:#C8972A;--gold-lt:#E8B84B;--ink:#0F1117;--paper:#F7F4EE;--mist:#E2DDD4;--text:#2A2820;--sub:#6B6458;--white:#fff}
*,*::before,*::after{box-sizing:border-box;margin:0;padding:0}
html{scroll-behavior:smooth}
body{font-family:'Cairo',sans-serif;background:var(--paper);color:var(--text);overflow-x:hidden}

/* NAV */
nav{position:fixed;top:0;width:100%;z-index:100;background:rgba(15,17,23,0.97);backdrop-filter:blur(12px);height:60px;display:flex;align-items:center;justify-content:space-between;padding:0 4%;border-bottom:1px solid rgba(200,151,42,0.2)}
.nav-logo{font-size:1.2rem;font-weight:900;color:var(--gold)}.nav-logo span{color:#fff}
.nav-links{display:flex;gap:0.5rem}
.nav-link{color:rgba(255,255,255,0.7);text-decoration:none;font-size:0.85rem;font-weight:600;padding:0.4rem 0.9rem;border-radius:8px;transition:all 0.2s;border:1px solid transparent;cursor:pointer;background:none}
.nav-link:hover,.nav-link.active{color:var(--gold);border-color:rgba(200,151,42,0.3);background:rgba(200,151,42,0.08)}
.admin-btn{background:transparent;border:1px solid rgba(200,151,42,0.3);color:var(--gold);padding:0.35rem 0.8rem;border-radius:6px;font-family:'Cairo',sans-serif;font-size:0.78rem;font-weight:600;cursor:pointer;transition:all 0.2s}
.admin-btn:hover{background:var(--gold);color:var(--ink)}

/* PAGES */
.page{display:none;min-height:100vh;padding-top:60px}
.page.active{display:block}

/* HOME */
.hero{min-height:calc(100vh - 60px);background:var(--ink);display:flex;align-items:center;justify-content:center;text-align:center;padding:2rem;position:relative;overflow:hidden}
.hero::before{content:'';position:absolute;inset:0;background:radial-gradient(ellipse 70% 70% at 50% 50%,rgba(200,151,42,0.1) 0%,transparent 70%);pointer-events:none}
.hero-content{max-width:600px;position:relative}
.hero-badge{display:inline-flex;align-items:center;gap:0.5rem;background:rgba(200,151,42,0.12);border:1px solid rgba(200,151,42,0.3);border-radius:100px;padding:0.3rem 1rem;font-size:0.8rem;color:var(--gold-lt);font-weight:600;margin-bottom:1.5rem}
.hero h1{font-size:clamp(2rem,6vw,3.5rem);font-weight:900;color:#fff;line-height:1.15;margin-bottom:1rem}
.hero h1 em{font-style:normal;color:var(--gold)}
.hero p{color:rgba(255,255,255,0.5);font-size:1rem;line-height:1.8;margin-bottom:2.5rem}
.hero-cards{display:grid;grid-template-columns:repeat(3,1fr);gap:1rem;margin-top:2rem}
.hero-card{background:rgba(255,255,255,0.04);border:1px solid rgba(255,255,255,0.08);border-radius:14px;padding:1.5rem 1rem;cursor:pointer;transition:all 0.25s;text-decoration:none}
.hero-card:hover{border-color:var(--gold);background:rgba(200,151,42,0.08);transform:translateY(-4px)}
.hero-card-icon{font-size:2rem;margin-bottom:0.8rem}
.hero-card-title{color:#fff;font-weight:800;font-size:0.95rem;margin-bottom:0.3rem}
.hero-card-desc{color:rgba(255,255,255,0.4);font-size:0.78rem;line-height:1.5}

/* PAGE HEADER */
.page-header{background:var(--ink);padding:3rem 5% 2rem;text-align:center}
.page-header h2{font-size:clamp(1.6rem,4vw,2.4rem);font-weight:900;color:#fff;margin-bottom:0.5rem}
.page-header p{color:rgba(255,255,255,0.45);font-size:0.9rem}
.page-header .ph-badge{display:inline-block;background:rgba(200,151,42,0.12);border:1px solid rgba(200,151,42,0.3);border-radius:100px;padding:0.2rem 0.8rem;font-size:0.75rem;color:var(--gold-lt);margin-bottom:0.8rem}

/* PRODUCTS GRID */
.products-section{padding:2.5rem 5%;max-width:1200px;margin:auto}
.filter-bar{display:flex;gap:0.6rem;flex-wrap:wrap;justify-content:center;margin-bottom:2rem}
.filter-btn{background:var(--mist);color:var(--sub);border:none;border-radius:100px;padding:0.45rem 1.1rem;font-family:'Cairo',sans-serif;font-weight:600;font-size:0.82rem;cursor:pointer;transition:all 0.2s}
.filter-btn.active,.filter-btn:hover{background:var(--gold);color:var(--ink)}
.products-grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(280px,1fr));gap:1.5rem}
.product-card{background:#fff;border-radius:14px;overflow:hidden;border:1px solid var(--mist);transition:all 0.25s;cursor:pointer}
.product-card:hover{transform:translateY(-5px);box-shadow:0 16px 40px rgba(0,0,0,0.1)}
.card-thumb{height:160px;display:flex;align-items:center;justify-content:center;font-size:3rem;overflow:hidden}
.card-thumb img{width:100%;height:100%;object-fit:cover}
.card-body{padding:1.2rem}
.card-tag{display:inline-block;background:rgba(200,151,42,0.1);color:#8B6620;font-size:0.7rem;font-weight:700;padding:0.2rem 0.6rem;border-radius:100px;margin-bottom:0.6rem}
.card-title{font-size:1rem;font-weight:800;margin-bottom:0.4rem}
.card-desc{color:var(--sub);font-size:0.82rem;line-height:1.6;margin-bottom:1rem;display:-webkit-box;-webkit-line-clamp:2;-webkit-box-orient:vertical;overflow:hidden}
.card-footer{display:flex;align-items:center;justify-content:space-between;border-top:1px solid var(--mist);padding-top:0.9rem}
.card-price{font-size:1rem;font-weight:900;color:var(--gold)}
.card-btn{background:var(--ink);color:#fff;border:none;border-radius:7px;padding:0.45rem 0.9rem;font-family:'Cairo',sans-serif;font-weight:700;font-size:0.8rem;cursor:pointer;transition:background 0.2s}
.card-btn:hover{background:var(--gold);color:var(--ink)}
.empty-state{text-align:center;padding:4rem 2rem;color:var(--sub);grid-column:1/-1}
.empty-state .ei{font-size:3rem;margin-bottom:1rem}

/* SUPPORT PAGE */
.support-section{padding:2.5rem 5%;max-width:900px;margin:auto}
.support-grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(250px,1fr));gap:1.5rem}
.support-card{background:#fff;border-radius:16px;padding:2rem;border:1px solid var(--mist);text-align:center;transition:all 0.25s;text-decoration:none;display:block}
.support-card:hover{transform:translateY(-5px);box-shadow:0 16px 40px rgba(0,0,0,0.08);border-color:var(--gold)}
.support-icon{font-size:3rem;margin-bottom:1rem}
.support-title{font-size:1.1rem;font-weight:900;color:var(--text);margin-bottom:0.5rem}
.support-desc{color:var(--sub);font-size:0.85rem;line-height:1.6;margin-bottom:1.5rem}
.support-wa-btn{background:#25D366;color:#fff;border:none;border-radius:10px;padding:0.7rem 1.5rem;font-family:'Cairo',sans-serif;font-weight:700;font-size:0.9rem;cursor:pointer;display:inline-flex;align-items:center;gap:0.5rem;transition:background 0.2s;text-decoration:none}
.support-wa-btn:hover{background:#1ebe5d}
.support-info{background:rgba(200,151,42,0.08);border:1px solid rgba(200,151,42,0.2);border-radius:12px;padding:1.2rem;margin-top:1.5rem;text-align:center}
.support-info p{color:var(--sub);font-size:0.85rem;margin-bottom:0.5rem}
.support-info strong{color:var(--gold);font-size:1.1rem}

/* MODAL */
.modal-overlay{position:fixed;inset:0;z-index:1000;background:rgba(0,0,0,0.75);backdrop-filter:blur(6px);display:none;align-items:center;justify-content:center;padding:5%}
.modal-overlay.open{display:flex}
.modal{background:#fff;border-radius:20px;max-width:580px;width:100%;padding:2rem;position:relative;max-height:90vh;overflow-y:auto;animation:slideUp 0.25s ease}
@keyframes slideUp{from{transform:translateY(30px);opacity:0}to{transform:translateY(0);opacity:1}}
.modal-close{position:absolute;top:1rem;left:1rem;background:var(--mist);border:none;border-radius:50%;width:34px;height:34px;font-size:1rem;cursor:pointer;display:flex;align-items:center;justify-content:center;color:var(--sub);transition:background 0.2s}
.modal-close:hover{background:var(--gold);color:var(--ink)}
.modal-img{width:100%;height:200px;object-fit:cover;border-radius:12px;margin-bottom:1rem}
.modal-gallery-main{margin-bottom:0.5rem}
.modal-gallery-thumbs{display:flex;gap:0.5rem;overflow-x:auto;padding-bottom:0.3rem;margin-bottom:1rem}
.mg-thumb{position:relative;width:56px;height:56px;border-radius:8px;overflow:hidden;flex-shrink:0;cursor:pointer;border:2px solid transparent;opacity:0.6;transition:all 0.2s}
.mg-thumb img,.mg-thumb video{width:100%;height:100%;object-fit:cover}
.mg-thumb.active{border-color:var(--gold);opacity:1}
.mg-play{position:absolute;inset:0;display:flex;align-items:center;justify-content:center;background:rgba(0,0,0,0.35);color:#fff;font-size:0.7rem}
.modal-files-list{display:flex;flex-direction:column;gap:0.5rem;margin-top:0.7rem}
.modal-file-item{width:100%}
.modal-icon{font-size:3rem;text-align:center;margin-bottom:1rem}
.modal-title{font-size:1.4rem;font-weight:900;text-align:center;margin-bottom:0.3rem}
.modal-price{text-align:center;font-size:1.2rem;font-weight:900;color:var(--gold);margin-bottom:1rem}
.modal-desc{color:var(--sub);font-size:0.88rem;line-height:1.7;margin-bottom:1rem}
.features-title{font-size:0.8rem;font-weight:700;color:var(--sub);text-transform:uppercase;letter-spacing:0.08em;margin-bottom:0.7rem}
.features-list{list-style:none;display:flex;flex-direction:column;gap:0.4rem;margin-bottom:1.5rem}
.features-list li{display:flex;gap:0.5rem;font-size:0.88rem;color:var(--text)}
.features-list li::before{content:'✓';color:var(--gold);font-weight:900;flex-shrink:0}
.modal-btns{display:flex;gap:0.8rem;flex-wrap:wrap}
.modal-btns a{flex:1;text-align:center;padding:0.8rem;border-radius:10px;font-family:'Cairo',sans-serif;font-weight:700;font-size:0.9rem;text-decoration:none;transition:all 0.2s;min-width:130px;display:flex;align-items:center;justify-content:center;gap:0.4rem}
.btn-wa{background:#25D366;color:#fff}.btn-wa:hover{background:#1ebe5d}
.btn-dl{background:var(--ink);color:#fff}.btn-dl:hover{background:var(--gold);color:var(--ink)}

/* LOGIN */
#loginModal,#changePassModal{position:fixed;inset:0;z-index:3000;background:rgba(0,0,0,0.9);backdrop-filter:blur(10px);display:none;align-items:center;justify-content:center}
#loginModal.open,#changePassModal.open{display:flex}
.login-box{background:#161b27;border:1px solid rgba(200,151,42,0.2);border-radius:20px;padding:2.5rem;max-width:360px;width:90%;text-align:center}
.login-box h2{color:#fff;font-size:1.3rem;font-weight:900;margin-bottom:0.4rem}
.login-box p{color:rgba(255,255,255,0.4);font-size:0.82rem;margin-bottom:1.8rem}
.login-field{background:rgba(255,255,255,0.06);border:1px solid rgba(255,255,255,0.12);border-radius:10px;padding:0.75rem 1rem;width:100%;color:#fff;font-family:'Cairo',sans-serif;font-size:0.9rem;outline:none;margin-bottom:0.9rem;text-align:right;transition:border-color 0.2s}
.login-field:focus{border-color:var(--gold)}
.login-btn{background:var(--gold);color:var(--ink);border:none;border-radius:10px;padding:0.8rem;width:100%;font-family:'Cairo',sans-serif;font-weight:900;font-size:0.95rem;cursor:pointer;transition:background 0.2s}
.login-btn:hover{background:var(--gold-lt)}
.login-error{color:#ef4444;font-size:0.82rem;margin-top:0.7rem;display:none}
.login-cancel{background:transparent;border:none;color:rgba(255,255,255,0.3);font-family:'Cairo',sans-serif;font-size:0.82rem;cursor:pointer;margin-top:0.8rem;display:block;width:100%}

/* ADMIN */
#adminPanel{display:none;position:fixed;inset:0;z-index:2000;background:#0F1117;overflow-y:auto}
#adminPanel.open{display:block}
.admin-header{background:rgba(200,151,42,0.08);border-bottom:1px solid rgba(200,151,42,0.2);padding:1rem 2rem;display:flex;align-items:center;justify-content:space-between;flex-wrap:wrap;gap:0.8rem}
.admin-header h2{color:var(--gold);font-size:1rem;font-weight:900}
.admin-tabs{display:flex;gap:0.5rem;flex-wrap:wrap}
.admin-tab{padding:0.4rem 1rem;border-radius:8px;border:1px solid rgba(255,255,255,0.15);background:transparent;color:rgba(255,255,255,0.5);font-family:'Cairo',sans-serif;font-weight:600;font-size:0.82rem;cursor:pointer;transition:all 0.2s}
.admin-tab.active,.admin-tab:hover{border-color:var(--gold);color:var(--gold);background:rgba(200,151,42,0.08)}
.a-btn{padding:0.4rem 1rem;border-radius:8px;border:none;font-family:'Cairo',sans-serif;font-weight:700;font-size:0.82rem;cursor:pointer;transition:all 0.2s}
.a-btn-gold{background:var(--gold);color:var(--ink)}.a-btn-gold:hover{background:var(--gold-lt)}
.a-btn-red{background:rgba(239,68,68,0.15);color:#ef4444;border:1px solid rgba(239,68,68,0.3)}.a-btn-red:hover{background:#ef4444;color:#fff}
.a-btn-outline{background:transparent;color:rgba(255,255,255,0.6);border:1px solid rgba(255,255,255,0.2)}.a-btn-outline:hover{border-color:var(--gold);color:var(--gold)}
.admin-body{padding:1.5rem;max-width:1100px;margin:auto}
.admin-section{display:none}.admin-section.active{display:block}
.admin-grid{display:grid;grid-template-columns:1fr 1.6fr;gap:1.5rem}
.admin-card{background:rgba(255,255,255,0.03);border:1px solid rgba(255,255,255,0.08);border-radius:14px;padding:1.3rem}
.admin-card h3{color:#fff;font-size:0.9rem;font-weight:800;margin-bottom:1rem;padding-bottom:0.7rem;border-bottom:1px solid rgba(255,255,255,0.08);display:flex;justify-content:space-between;align-items:center}
.admin-card h3 span{color:var(--gold);font-size:0.78rem}
.form-group{margin-bottom:0.9rem}
.form-group label{display:block;color:rgba(255,255,255,0.5);font-size:0.78rem;font-weight:600;margin-bottom:0.35rem}
.form-group input,.form-group textarea,.form-group select{width:100%;background:rgba(255,255,255,0.06);border:1px solid rgba(255,255,255,0.12);border-radius:8px;padding:0.6rem 0.85rem;color:#fff;font-family:'Cairo',sans-serif;font-size:0.85rem;outline:none;transition:border-color 0.2s}
.form-group input:focus,.form-group textarea:focus,.form-group select:focus{border-color:var(--gold)}
.form-group textarea{resize:vertical;min-height:70px}
.form-group select option{background:#1a1f2e}
.features-wrap{display:flex;flex-direction:column;gap:0.4rem}
.feature-row{display:flex;gap:0.4rem}
.feature-row input{flex:1}
.feature-row button{background:rgba(239,68,68,0.2);border:none;border-radius:6px;color:#ef4444;padding:0 0.6rem;cursor:pointer;min-width:28px}
.add-feat-btn{background:rgba(200,151,42,0.08);border:1px dashed rgba(200,151,42,0.3);border-radius:7px;color:var(--gold);padding:0.4rem;font-family:'Cairo',sans-serif;font-weight:600;font-size:0.8rem;cursor:pointer;width:100%;margin-top:0.4rem}
.upload-area{border:2px dashed rgba(200,151,42,0.3);border-radius:9px;padding:1rem;text-align:center;cursor:pointer;transition:all 0.2s}
.upload-area:hover{border-color:var(--gold);background:rgba(200,151,42,0.04)}
.upload-area p{color:rgba(255,255,255,0.3);font-size:0.78rem;margin-top:0.3rem}
.upload-area .up-icon{font-size:1.6rem}
.progress-bar-bg{background:rgba(255,255,255,0.08);border-radius:6px;height:5px;overflow:hidden;margin-top:0.7rem;display:none}
.progress-bar-fill{background:var(--gold);height:100%;width:0%;transition:width 0.2s}
.img-prev{width:100%;height:90px;object-fit:cover;border-radius:7px;margin-top:0.7rem;display:none}
.admin-item{background:rgba(255,255,255,0.04);border:1px solid rgba(255,255,255,0.07);border-radius:9px;padding:0.8rem;margin-bottom:0.6rem;display:flex;gap:0.7rem;align-items:center;transition:border-color 0.2s}
.admin-item:hover{border-color:rgba(200,151,42,0.3)}
.admin-thumb{width:44px;height:44px;border-radius:7px;flex-shrink:0;display:flex;align-items:center;justify-content:center;font-size:1.4rem;background:rgba(255,255,255,0.05);overflow:hidden}
.admin-thumb img{width:100%;height:100%;object-fit:cover}
.admin-info{flex:1;min-width:0}
.ai-title{color:#fff;font-weight:700;font-size:0.85rem;white-space:nowrap;overflow:hidden;text-overflow:ellipsis}
.ai-sub{color:rgba(255,255,255,0.35);font-size:0.72rem;margin-top:2px}
.admin-actions{display:flex;gap:0.4rem;flex-shrink:0}
.a-icon-btn{background:transparent;border:1px solid rgba(255,255,255,0.1);border-radius:6px;color:rgba(255,255,255,0.4);padding:0.3rem 0.5rem;cursor:pointer;font-size:0.8rem;transition:all 0.2s}
.a-icon-btn.edit:hover{border-color:var(--gold);color:var(--gold)}
.a-icon-btn.del:hover{border-color:#ef4444;color:#ef4444}

/* ACTIVATION MODAL */
#activationModal{position:fixed;inset:0;z-index:4000;background:rgba(0,0,0,0.9);backdrop-filter:blur(10px);display:none;align-items:center;justify-content:center}
#activationModal.open{display:flex}
.activation-box{background:#161b27;border:1px solid rgba(200,151,42,0.3);border-radius:20px;padding:2.5rem;max-width:380px;width:90%;text-align:center}
.activation-box h2{color:#fff;font-size:1.2rem;font-weight:900;margin-bottom:0.4rem}
.activation-box p{color:rgba(255,255,255,0.4);font-size:0.82rem;margin-bottom:1.5rem;line-height:1.7}
.activation-steps{background:rgba(200,151,42,0.08);border:1px solid rgba(200,151,42,0.2);border-radius:12px;padding:1rem;margin-bottom:1.5rem;text-align:right}
.activation-steps p{color:rgba(255,255,255,0.6);font-size:0.82rem;margin-bottom:0.4rem}
.activation-steps strong{color:var(--gold)}
.activation-field{background:rgba(255,255,255,0.06);border:1px solid rgba(255,255,255,0.12);border-radius:10px;padding:0.75rem 1rem;width:100%;color:#fff;font-family:'Cairo',sans-serif;font-size:0.9rem;outline:none;margin-bottom:0.9rem;text-align:center;letter-spacing:0.15em;transition:border-color 0.2s}
.activation-field:focus{border-color:var(--gold)}
.activation-btn{background:var(--gold);color:var(--ink);border:none;border-radius:10px;padding:0.8rem;width:100%;font-family:'Cairo',sans-serif;font-weight:900;font-size:0.95rem;cursor:pointer;margin-bottom:0.7rem;transition:background 0.2s}
.activation-btn:hover{background:var(--gold-lt)}
.activation-wa{background:#25D366;color:#fff;border:none;border-radius:10px;padding:0.7rem;width:100%;font-family:'Cairo',sans-serif;font-weight:700;font-size:0.88rem;cursor:pointer;margin-bottom:0.7rem;transition:background 0.2s;display:flex;align-items:center;justify-content:center;gap:0.5rem;text-decoration:none}
.activation-wa:hover{background:#1ebe5d}
.activation-cancel{background:transparent;border:none;color:rgba(255,255,255,0.3);font-family:'Cairo',sans-serif;font-size:0.82rem;cursor:pointer;width:100%}
.activation-error{color:#ef4444;font-size:0.82rem;margin-bottom:0.7rem;display:none}

/* TOAST */
.toast{position:fixed;bottom:2rem;left:50%;transform:translateX(-50%) translateY(100px);background:#1a2e1a;border:1px solid #2d5a2d;color:#86efac;padding:0.7rem 1.3rem;border-radius:10px;font-weight:600;font-size:0.88rem;z-index:9999;transition:transform 0.3s;pointer-events:none;white-space:nowrap}
.toast.show{transform:translateX(-50%) translateY(0)}
.toast.error{background:#2e1a1a;border-color:#5a2d2d;color:#fca5a5}
.spinner{width:28px;height:28px;border:3px solid rgba(200,151,42,0.2);border-top-color:var(--gold);border-radius:50%;animation:spin 0.8s linear infinite;margin:1.5rem auto}
@keyframes spin{to{transform:rotate(360deg)}}

/* FOOTER */
footer{background:#080A0E;color:rgba(255,255,255,0.3);text-align:center;padding:1.2rem 5%;font-size:0.8rem}
footer span{color:var(--gold)}

@media(max-width:768px){
  .hero-cards{grid-template-columns:1fr}
  .nav-links{gap:0.3rem}
  .nav-link{font-size:0.78rem;padding:0.35rem 0.6rem}
  .admin-grid{grid-template-columns:1fr}
  .products-grid{grid-template-columns:1fr}
}
</style>
</head>
<body>

<!-- NAV -->
<nav>
  <div class="nav-logo">مينا <span>للبرمجة</span></div>
  <div class="nav-links">
    <button class="nav-link active" onclick="showPage('home',this)">الرئيسية</button>
    <button class="nav-link" onclick="showPage('projects',this)">المشاريع</button>
    <button class="nav-link" onclick="showPage('store',this)">المتجر</button>
    <button class="nav-link" onclick="showPage('media',this)">الوسائط</button>
    <button class="nav-link" onclick="showPage('support',this)">الدعم الفني</button>
  </div>
  <button class="admin-btn" onclick="openLogin()">🔐 إدارة</button>
</nav>

<!-- HOME PAGE -->
<div class="page active" id="page-home">
  <div class="hero">
    <div class="hero-content">
      <div class="hero-badge">● حلول رقمية مصرية · صعيد مصر</div>
      <h1>مرحباً بك في<br><em>مينا للبرمجة</em></h1>
      <p>مشاريع برمجية، وسائط، متجر، ودعم فني — كل ما تحتاجه في مكان واحد</p>
      <div class="hero-cards">
        <div class="hero-card" onclick="showPage('projects',null)">
          <div class="hero-card-icon">💻</div>
          <div class="hero-card-title">المشاريع</div>
          <div class="hero-card-desc">أنظمة برمجية جاهزة للتسليم الفوري</div>
        </div>
        <div class="hero-card" onclick="showPage('store',null)">
          <div class="hero-card-icon">🛒</div>
          <div class="hero-card-title">المتجر</div>
          <div class="hero-card-desc">منتجات متنوعة للبيع بأسعار مناسبة</div>
        </div>
        <div class="hero-card" onclick="showPage('media',null)">
          <div class="hero-card-icon">🎬</div>
          <div class="hero-card-title">الوسائط</div>
          <div class="hero-card-desc">صور، فيديوهات، وملفات صوتية</div>
        </div>
        <div class="hero-card" onclick="showPage('support',null)">
          <div class="hero-card-icon">🛠️</div>
          <div class="hero-card-title">الدعم الفني</div>
          <div class="hero-card-desc">دعم برمجة، كمبيوتر، وتركيب دشات</div>
        </div>
      </div>
    </div>
  </div>
  <footer><p>© ٢٠٢٥ <span>مينا للبرمجة</span> · صعيد مصر · جميع الحقوق محفوظة</p></footer>
</div>

<!-- PROJECTS PAGE -->
<div class="page" id="page-projects">
  <div class="page-header">
    <div class="ph-badge">المشاريع البرمجية</div>
    <h2>أنظمة جاهزة للتسليم</h2>
    <p>أنظمة برمجية جاهزة للتسليم الفوري</p>
  </div>
  <div class="products-section">
    <div class="filter-bar">
      <button class="filter-btn active" onclick="filterProducts('all',this,'projects')">الكل</button>
      <button class="filter-btn" onclick="filterProducts('medical',this,'projects')">طب</button>
      <button class="filter-btn" onclick="filterProducts('church',this,'projects')">كنيسة</button>
      <button class="filter-btn" onclick="filterProducts('business',this,'projects')">أعمال</button>
      <button class="filter-btn" onclick="filterProducts('other',this,'projects')">أخرى</button>
    </div>
    <div class="products-grid" id="projectsGrid">
      <div style="grid-column:1/-1;text-align:center;padding:2rem"><div class="spinner"></div></div>
    </div>
  </div>
  <footer><p>© ٢٠٢٥ <span>مينا للبرمجة</span> · جميع الحقوق محفوظة</p></footer>
</div>

<!-- STORE PAGE -->
<div class="page" id="page-store">
  <div class="page-header">
    <div class="ph-badge">المتجر الإلكتروني</div>
    <h2>منتجاتنا المتنوعة</h2>
    <p>أجهزة، إكسسوارات، ومنتجات متنوعة بأسعار مناسبة</p>
  </div>
  <div class="products-section">
    <div class="filter-bar">
      <button class="filter-btn active" onclick="filterProducts('all',this,'store')">الكل</button>
      <button class="filter-btn" onclick="filterProducts('satellite',this,'store')">فضائيات</button>
      <button class="filter-btn" onclick="filterProducts('electronics',this,'store')">إلكترونيات</button>
      <button class="filter-btn" onclick="filterProducts('accessories',this,'store')">إكسسوارات</button>
      <button class="filter-btn" onclick="filterProducts('other',this,'store')">أخرى</button>
    </div>
    <div class="products-grid" id="storeGrid">
      <div style="grid-column:1/-1;text-align:center;padding:2rem"><div class="spinner"></div></div>
    </div>
  </div>
  <footer><p>© ٢٠٢٥ <span>مينا للبرمجة</span> · جميع الحقوق محفوظة</p></footer>
</div>


<!-- MEDIA PAGE -->
<div class="page" id="page-media">
  <div class="page-header">
    <div class="ph-badge">الوسائط</div>
    <h2>صور، فيديوهات، وصوتيات</h2>
    <p>تصفح مكتبة الوسائط المتاحة</p>
  </div>
  <div class="products-section">
    <div class="filter-bar">
      <button class="filter-btn active" onclick="filterMedia('all',this)">الكل</button>
      <button class="filter-btn" onclick="filterMedia('image',this)">صور 🖼️</button>
      <button class="filter-btn" onclick="filterMedia('video',this)">فيديو 🎬</button>
      <button class="filter-btn" onclick="filterMedia('audio',this)">صوت 🎵</button>
      <button class="filter-btn" onclick="filterMedia('other',this)">أخرى</button>
    </div>
    <div class="products-grid" id="mediaGrid">
      <div style="grid-column:1/-1;text-align:center;padding:2rem"><div class="spinner"></div></div>
    </div>
  </div>
  <footer><p>© ٢٠٢٥ <span>مينا للبرمجة</span> · جميع الحقوق محفوظة</p></footer>
</div>

<!-- SUPPORT PAGE -->
<div class="page" id="page-support">
  <div class="page-header">
    <div class="ph-badge">الدعم الفني</div>
    <h2>جاهزين نساعدك</h2>
    <p>تواصل معنا عبر واتساب وهنرد في أسرع وقت</p>
  </div>
  <div class="support-section">
    <div class="support-grid">
      <a class="support-card" href="https://wa.me/201227016225?text=أهلاً، محتاج دعم فني في البرمجة" target="_blank">
        <div class="support-icon">💻</div>
        <div class="support-title">دعم البرمجة</div>
        <div class="support-desc">مساعدة في المشاريع البرمجية، الأنظمة، وتطوير المواقع</div>
        <span class="support-wa-btn">💬 تواصل واتساب</span>
      </a>
      <a class="support-card" href="https://wa.me/201227016225?text=أهلاً، محتاج دعم فني في الكمبيوتر" target="_blank">
        <div class="support-icon">🖥️</div>
        <div class="support-title">دعم الكمبيوتر</div>
        <div class="support-desc">صيانة وحل مشاكل الكمبيوتر، تنظيف، وتركيب برامج</div>
        <span class="support-wa-btn">💬 تواصل واتساب</span>
      </a>
      <a class="support-card" href="https://wa.me/201227016225?text=أهلاً، محتاج دعم فني في تركيب الدشات" target="_blank">
        <div class="support-icon">📡</div>
        <div class="support-title">تركيب الدشات</div>
        <div class="support-desc">تركيب وصيانة الأطباق الفضائية وضبط الترددات</div>
        <span class="support-wa-btn">💬 تواصل واتساب</span>
      </a>
    </div>
    <div class="support-info">
      <p>للتواصل المباشر</p>
      <strong>📞 01227016225</strong>
    </div>
  </div>
  <footer><p>© ٢٠٢٥ <span>مينا للبرمجة</span> · جميع الحقوق محفوظة</p></footer>
</div>

<!-- PRODUCT MODAL -->
<div class="modal-overlay" id="modalOverlay" onclick="closeModal(event)">
  <div class="modal">
    <button class="modal-close" onclick="closeModal()">✕</button>
    <div id="modalBody"></div>
  </div>
</div>

<!-- ACTIVATION MODAL -->
<div id="activationModal">
  <div class="activation-box">
    <div style="font-size:2.5rem;margin-bottom:0.8rem">🔐</div>
    <h2>تفعيل التحميل</h2>
    <p>هذا الملف محمي<br>للتحميل تحتاج كود تفعيل خاص</p>
    <div class="activation-steps">
      <p>📱 تواصل معنا على واتساب</p>
      <p>💳 أتم عملية الدفع</p>
      <p>📩 احصل على <strong>كود التفعيل</strong></p>
    </div>
    <input type="text" class="activation-field" id="activationCode" placeholder="أدخل كود التفعيل هنا">
    <p class="activation-error" id="activationError">❌ الكود غير صحيح، تواصل معنا</p>
    <button class="activation-btn" onclick="checkActivationCode()">✅ تفعيل وتحميل</button>
    <a id="activationWaBtn" href="" target="_blank" class="activation-wa">💬 تواصل واتساب للحصول على الكود</a>
    <button class="activation-cancel" onclick="closeActivation()">إلغاء</button>
  </div>
</div>

<!-- LOGIN -->
<div id="loginModal">
  <div class="login-box">
    <div style="font-size:2.5rem;margin-bottom:0.8rem">🔐</div>
    <h2>لوحة التحكم</h2>
    <p>ادخل بياناتك للوصول للإدارة</p>
    <input type="email" class="login-field" id="loginEmail" placeholder="الإيميل" dir="ltr">
    <input type="password" class="login-field" id="loginPass" placeholder="كلمة السر" dir="ltr">
    <button class="login-btn" id="loginBtn" onclick="doLogin()">دخول</button>
    <p class="login-error" id="loginError">إيميل أو كلمة سر غلط</p>
    <button class="login-cancel" onclick="closeLogin()">إلغاء</button>
  </div>
</div>

<!-- CHANGE PASSWORD -->
<div id="changePassModal">
  <div class="login-box">
    <div style="font-size:2.5rem;margin-bottom:0.8rem">🔑</div>
    <h2>تغيير كلمة السر</h2>
    <p>أدخل كلمة السر الحالية والجديدة</p>
    <input type="password" class="login-field" id="cpCurrent" placeholder="كلمة السر الحالية" dir="ltr">
    <input type="password" class="login-field" id="cpNew" placeholder="كلمة السر الجديدة (٨ أحرف فأكثر)" dir="ltr">
    <input type="password" class="login-field" id="cpConfirm" placeholder="تأكيد كلمة السر الجديدة" dir="ltr">
    <button class="login-btn" id="cpBtn" onclick="doChangePass()">تحديث</button>
    <p class="login-error" id="cpError"></p>
    <p class="login-error" id="cpSuccess" style="color:#86efac"></p>
    <button class="login-cancel" onclick="closeChangePass()">إلغاء</button>
  </div>
</div>

<!-- ADMIN PANEL -->
<div id="adminPanel">
  <div class="admin-header">
    <h2>🛠️ لوحة التحكم</h2>
    <div class="admin-tabs">
      <button class="admin-tab active" onclick="switchAdminTab('projects-admin',this)">💻 المشاريع</button>
      <button class="admin-tab" onclick="switchAdminTab('store-admin',this)">🛒 المتجر</button>
      <button class="admin-tab" onclick="switchAdminTab('media-admin',this)">🎬 الوسائط</button>
    </div>
    <div style="display:flex;gap:0.5rem">
      <button class="a-btn a-btn-outline" onclick="resetForm()">+ جديد</button>
      <button class="a-btn a-btn-outline" onclick="openChangePass()">🔑 كلمة السر</button>
      <button class="a-btn a-btn-red" onclick="doLogout()">خروج</button>
    </div>
  </div>
  <div class="admin-body">

    <!-- PROJECTS ADMIN -->
    <div class="admin-section active" id="admin-projects-admin">
      <div class="admin-grid">
        <div class="admin-card">
          <h3 id="formTitle">➕ إضافة مشروع</h3>
          <input type="hidden" id="editId">
          <input type="hidden" id="editSection">
          <div class="form-group"><label>الاسم *</label><input type="text" id="fTitle" placeholder="اسم المشروع"></div>
          <div class="form-group"><label>الوصف *</label><textarea id="fDesc" placeholder="وصف مختصر..."></textarea></div>
          <div class="form-group"><label>السعر *</label><input type="text" id="fPrice" placeholder="مثال: ٢٠٠٠ ج.م"></div>
          <div class="form-group">
            <label>التصنيف</label>
            <select id="fCat">
              <option value="medical">طب</option>
              <option value="church">كنيسة</option>
              <option value="business">أعمال</option>
              <option value="satellite">فضائيات</option>
              <option value="electronics">إلكترونيات</option>
              <option value="accessories">إكسسوارات</option>
              <option value="other">أخرى</option>
            </select>
          </div>
          <div class="form-group"><label>الإيموجي</label><input type="text" id="fEmoji" placeholder="مثال: 🏥"></div>
          <div class="form-group">
            <label>الصور / الفيديوهات (تقدر تختار أكتر من ملف مرة واحدة) <span id="galCount" style="color:var(--gold);font-weight:700"></span></label>
            <div class="upload-area" onclick="document.getElementById('fImg').click()">
              <div class="up-icon">🖼️</div>
              <p id="imgTxt">اضغط لرفع صور / فيديوهات (يمكن اختيار أكثر من ملف)</p>
              <div class="progress-bar-bg" id="imgProg"><div class="progress-bar-fill" id="imgProgFill"></div></div>
            </div>
            <div id="galPreviewWrap" style="display:flex;flex-wrap:wrap;gap:0.5rem;margin-top:0.7rem"></div>
            <input type="file" id="fImg" accept="image/*,video/*" multiple style="display:none" onchange="handleImg(this)">
          </div>
          <div class="form-group">
            <label>ملفات التحميل (اختياري - يمكن اختيار أكثر من ملف) <span id="fileCount" style="color:var(--gold);font-weight:700"></span></label>
            <div class="upload-area" onclick="document.getElementById('fFile').click()">
              <div class="up-icon">📁</div>
              <p id="fileTxt">اضغط لرفع ملف أو أكثر (مشروع متكامل)</p>
              <div class="progress-bar-bg" id="fileProg"><div class="progress-bar-fill" id="fileProgFill"></div></div>
            </div>
            <div id="filePreviewWrap" style="display:flex;flex-direction:column;gap:0.4rem;margin-top:0.6rem"></div>
            <input type="file" id="fFile" multiple style="display:none" onchange="handleFile(this)">
          </div>
          <div class="form-group">
            <label>المميزات</label>
            <div class="features-wrap" id="featWrap">
              <div class="feature-row"><input type="text" placeholder="ميزة..."><button onclick="this.parentElement.remove()">✕</button></div>
            </div>
            <button class="add-feat-btn" onclick="addFeat()">+ إضافة ميزة</button>
          </div>
          <div class="form-group"><label>رقم واتساب</label><input type="text" id="fWa" value="201227016225" dir="ltr"></div>
          <div class="form-group">
            <label>🔐 كود التحميل (اكتب أي كود تحبه - ابعته للعميل بعد الدفع)</label>
            <input type="text" id="fCode" placeholder="مثال: ABC123 أو MOK2025" dir="ltr" style="letter-spacing:0.1em">
            <p style="color:rgba(255,255,255,0.3);font-size:0.75rem;margin-top:0.4rem">⚠️ لو مكتبتش كود، التحميل هيكون مجاني بدون حماية</p>
          </div>
          <div style="display:flex;gap:0.7rem;margin-top:1rem">
            <button class="a-btn a-btn-gold" style="flex:1" onclick="saveProduct()">💾 حفظ</button>
            <button class="a-btn a-btn-outline" onclick="resetForm()">إلغاء</button>
          </div>
        </div>
        <div class="admin-card">
          <h3>المشاريع <span id="projCount"></span></h3>
          <div id="adminProjList"><div class="spinner"></div></div>
        </div>
      </div>
    </div>

    <!-- STORE ADMIN -->
    <div class="admin-section" id="admin-store-admin">
      <div class="admin-grid">
        <div class="admin-card">
          <h3 id="storeFormTitle">➕ إضافة منتج</h3>
          <p style="color:rgba(255,255,255,0.4);font-size:0.82rem;text-align:center;padding:1rem">اضغط + جديد من فوق لإضافة منتج للمتجر</p>
        </div>
        <div class="admin-card">
          <h3>منتجات المتجر <span id="storeCount"></span></h3>
          <div id="adminStoreList"><div class="spinner"></div></div>
        </div>
      </div>
    </div>


    <!-- MEDIA ADMIN -->
    <div class="admin-section" id="admin-media-admin">
      <div class="admin-grid">
        <div class="admin-card">
          <h3 id="mediaFormTitle">➕ إضافة وسيط</h3>
          <div class="form-group"><label>العنوان *</label><input type="text" id="mTitle" placeholder="عنوان الملف"></div>
          <div class="form-group"><label>الوصف</label><textarea id="mDesc" placeholder="وصف مختصر..."></textarea></div>
          <div class="form-group">
            <label>النوع</label>
            <select id="mType">
              <option value="image">صورة 🖼️</option>
              <option value="video">فيديو 🎬</option>
              <option value="audio">صوت 🎵</option>
              <option value="other">أخرى</option>
            </select>
          </div>
          <div class="form-group">
            <label>رفع الملف *</label>
            <div class="upload-area" onclick="document.getElementById('mFile').click()">
              <div class="up-icon" id="mUpIcon">📁</div>
              <p id="mFileTxt">اضغط لرفع صورة / فيديو / صوت</p>
              <div class="progress-bar-bg" id="mFileProg"><div class="progress-bar-fill" id="mFileProgFill"></div></div>
            </div>
            <input type="file" id="mFile" accept="image/*,video/*,audio/*" style="display:none" onchange="handleMediaFile(this)">
          </div>
          <div class="form-group">
            <label>صورة مصغرة (للفيديو والصوت)</label>
            <div class="upload-area" onclick="document.getElementById('mThumb').click()">
              <div class="up-icon">🖼️</div>
              <p id="mThumbTxt">صورة غلاف (اختياري)</p>
              <div class="progress-bar-bg" id="mThumbProg"><div class="progress-bar-fill" id="mThumbProgFill"></div></div>
              <img id="mThumbPrev" class="img-prev">
            </div>
            <input type="file" id="mThumb" accept="image/*" style="display:none" onchange="handleMediaThumb(this)">
          </div>
          <div style="display:flex;gap:0.7rem;margin-top:1rem">
            <button class="a-btn a-btn-gold" style="flex:1" onclick="saveMedia()">💾 حفظ</button>
            <button class="a-btn a-btn-outline" onclick="resetMediaForm()">إلغاء</button>
          </div>
        </div>
        <div class="admin-card">
          <h3>الوسائط <span id="mediaCount"></span></h3>
          <div id="adminMediaList"><div class="spinner"></div></div>
        </div>
      </div>
    </div>
  </div>
</div>

<div class="toast" id="toast"></div>

<script>
// Global bridge - these functions will be assigned by the module
window._bridge = {};
function showPage(p,b){ if(window._bridge.showPage) window._bridge.showPage(p,b); }
function filterProducts(c,b,t){ if(window._bridge.filterProducts) window._bridge.filterProducts(c,b,t); }
function filterMedia(c,b){ if(window._bridge.filterMedia) window._bridge.filterMedia(c,b); }
function openModal(id,t){ if(window._bridge.openModal) window._bridge.openModal(id,t); }
function openMediaModal(id){ if(window._bridge.openMediaModal) window._bridge.openMediaModal(id); }
function closeModal(e){ if(window._bridge.closeModal) window._bridge.closeModal(e); }
function openLogin(){ if(window._bridge.openLogin) window._bridge.openLogin(); }
function closeLogin(){ if(window._bridge.closeLogin) window._bridge.closeLogin(); }
function doLogin(){ if(window._bridge.doLogin) window._bridge.doLogin(); }
function doLogout(){ if(window._bridge.doLogout) window._bridge.doLogout(); }
function switchAdminTab(s,b){ if(window._bridge.switchAdminTab) window._bridge.switchAdminTab(s,b); }
function saveProduct(){ if(window._bridge.saveProduct) window._bridge.saveProduct(); }
function editItem(id,t){ if(window._bridge.editItem) window._bridge.editItem(id,t); }
function deleteItem(id,t){ if(window._bridge.deleteItem) window._bridge.deleteItem(id,t); }
function resetForm(){ if(window._bridge.resetForm) window._bridge.resetForm(); }
function addFeat(){ if(window._bridge.addFeat) window._bridge.addFeat(); }
function handleImg(i){ if(window._bridge.handleImg) window._bridge.handleImg(i); }
function handleFile(i){ if(window._bridge.handleFile) window._bridge.handleFile(i); }
function saveMedia(){ if(window._bridge.saveMedia) window._bridge.saveMedia(); }
function deleteMedia(id){ if(window._bridge.deleteMedia) window._bridge.deleteMedia(id); }
function resetMediaForm(){ if(window._bridge.resetMediaForm) window._bridge.resetMediaForm(); }
function handleMediaFile(i){ if(window._bridge.handleMediaFile) window._bridge.handleMediaFile(i); }
function handleMediaThumb(i){ if(window._bridge.handleMediaThumb) window._bridge.handleMediaThumb(i); }
function showToast(m,e){ if(window._bridge.showToast) window._bridge.showToast(m,e); }
</script>
<script type="module">
import { initializeApp } from "https://www.gstatic.com/firebasejs/10.12.0/firebase-app.js";
import { getAuth, signInWithEmailAndPassword, signOut, onAuthStateChanged, EmailAuthProvider, reauthenticateWithCredential, updatePassword } from "https://www.gstatic.com/firebasejs/10.12.0/firebase-auth.js";
import { getFirestore, collection, addDoc, getDocs, updateDoc, deleteDoc, doc, orderBy, query, serverTimestamp } from "https://www.gstatic.com/firebasejs/10.12.0/firebase-firestore.js";

const firebaseConfig = {
  apiKey: "AIzaSyAtSEqHUg1G81ReynWCImQurttmeyqblhM",
  authDomain: "meena-253b3.firebaseapp.com",
  projectId: "meena-253b3",
  storageBucket: "meena-253b3.firebasestorage.app",
  messagingSenderId: "612273445379",
  appId: "1:612273445379:web:33b2fcd882616feaa5cc36"
};

const CLOUD = "dytbyf8na";
const PRESET = "meena_uploads";
const ADMIN_UID = "NI0iubPtIcOd8h6tLeZ8vn4MHve2";

const app = initializeApp(firebaseConfig);
const auth = getAuth(app);
const db = getFirestore(app);

let projects = [], storeItems = [];
let currentFilter = { projects: 'all', store: 'all' };
let galleryUrls = [], fileUrls = [];
let currentAdminSection = 'projects';

// ── NAVIGATION ──
window._bridge.showPage = window.showPage = (page, btn) => {
  document.querySelectorAll('.page').forEach(p => p.classList.remove('active'));
  document.getElementById('page-' + page).classList.add('active');
  document.querySelectorAll('.nav-link').forEach(b => b.classList.remove('active'));
  if (btn) btn.classList.add('active');
  else document.querySelectorAll('.nav-link').forEach(b => { if (b.textContent.includes(pageNames[page])) b.classList.add('active'); });
  window.scrollTo(0, 0);
};
const pageNames = { home: 'الرئيسية', projects: 'المشاريع', store: 'المتجر', support: 'الدعم' };

window._bridge.switchAdminTab = window.switchAdminTab = (section, btn) => {
  document.querySelectorAll('.admin-section').forEach(s => s.classList.remove('active'));
  document.getElementById('admin-' + section).classList.add('active');
  document.querySelectorAll('.admin-tab').forEach(b => b.classList.remove('active'));
  btn.classList.add('active');
  currentAdminSection = section === 'projects-admin' ? 'projects' : section === 'store-admin' ? 'store' : 'media';
  resetForm();
};

// ── AUTH ──
window._bridge.openLogin = window.openLogin = () => document.getElementById('loginModal').classList.add('open');
window._bridge.closeLogin = window.closeLogin = () => document.getElementById('loginModal').classList.remove('open');

window.doLogin = async () => {
  const email = document.getElementById('loginEmail').value.trim();
  const pass = document.getElementById('loginPass').value;
  const err = document.getElementById('loginError');
  const btn = document.getElementById('loginBtn');
  err.style.display = 'none'; btn.textContent = 'جاري الدخول...'; btn.disabled = true;
  try {
    const cred = await signInWithEmailAndPassword(auth, email, pass);
    if (cred.user.uid !== ADMIN_UID) { await signOut(auth); err.textContent = 'ليس حساب المدير'; err.style.display = 'block'; }
  } catch(e) { err.style.display = 'block'; }
  finally { btn.textContent = 'دخول'; btn.disabled = false; }
};

window.doLogout = async () => {
  await signOut(auth);
  document.getElementById('adminPanel').classList.remove('open');
  showToast('تم تسجيل الخروج');
};

// ── CHANGE PASSWORD ──
window._bridge.openChangePass = window.openChangePass = () => {
  document.getElementById('cpCurrent').value = '';
  document.getElementById('cpNew').value = '';
  document.getElementById('cpConfirm').value = '';
  document.getElementById('cpError').style.display = 'none';
  document.getElementById('cpSuccess').style.display = 'none';
  document.getElementById('changePassModal').classList.add('open');
};
window._bridge.closeChangePass = window.closeChangePass = () => document.getElementById('changePassModal').classList.remove('open');

window.doChangePass = async () => {
  const current = document.getElementById('cpCurrent').value;
  const newPass = document.getElementById('cpNew').value;
  const confirm = document.getElementById('cpConfirm').value;
  const err = document.getElementById('cpError');
  const ok = document.getElementById('cpSuccess');
  const btn = document.getElementById('cpBtn');
  err.style.display = 'none'; ok.style.display = 'none';

  if (!current || !newPass || !confirm) { err.textContent = 'من فضلك اكمل كل الخانات'; err.style.display = 'block'; return; }
  if (newPass.length < 8) { err.textContent = 'كلمة السر الجديدة لازم تكون ٨ أحرف على الأقل'; err.style.display = 'block'; return; }
  if (newPass !== confirm) { err.textContent = 'كلمة السر الجديدة وتأكيدها غير متطابقين'; err.style.display = 'block'; return; }

  btn.textContent = 'جاري التحديث...'; btn.disabled = true;
  try {
    const user = auth.currentUser;
    const credential = EmailAuthProvider.credential(user.email, current);
    await reauthenticateWithCredential(user, credential);
    await updatePassword(user, newPass);
    ok.textContent = 'تم تغيير كلمة السر بنجاح ✅'; ok.style.display = 'block';
    document.getElementById('cpCurrent').value = '';
    document.getElementById('cpNew').value = '';
    document.getElementById('cpConfirm').value = '';
  } catch (e) {
    let msg = 'حدث خطأ، حاول مرة أخرى';
    if (e.code === 'auth/invalid-credential' || e.code === 'auth/wrong-password') msg = 'كلمة السر الحالية غير صحيحة';
    else if (e.code === 'auth/weak-password') msg = 'كلمة السر الجديدة ضعيفة جدًا';
    else if (e.code === 'auth/requires-recent-login') msg = 'يجب تسجيل الخروج والدخول مرة أخرى قبل تغيير كلمة السر';
    err.textContent = msg; err.style.display = 'block';
  } finally {
    btn.textContent = 'تحديث'; btn.disabled = false;
  }
};

onAuthStateChanged(auth, user => {
  if (user && user.uid === ADMIN_UID) {
    document.getElementById('loginModal').classList.remove('open');
    document.getElementById('adminPanel').classList.add('open');
    loadAll();
  }
});

// ── LOAD DATA ──
async function loadAll() {
  await loadCollection('projects');
  await loadCollection('store');
  await loadMedia();
}

async function loadCollection(col) {
  try {
    const q = query(collection(db, col), orderBy('createdAt', 'desc'));
    const snap = await getDocs(q);
    const items = snap.docs.map(d => ({ id: d.id, ...d.data() }));
    if (col === 'projects') { projects = items; renderPublic('projects'); renderAdminList('projects'); }
    else { storeItems = items; renderPublic('store'); renderAdminList('store'); }
  } catch(e) {
    if (col === 'projects') document.getElementById('projectsGrid').innerHTML = '<div style="grid-column:1/-1;text-align:center;color:#888;padding:2rem">تعذر التحميل</div>';
  }
}

async function loadPublicOnly() {
  try {
    const pq = query(collection(db, 'projects'), orderBy('createdAt', 'desc'));
    const sq = query(collection(db, 'store'), orderBy('createdAt', 'desc'));
    const [ps, ss] = await Promise.all([getDocs(pq), getDocs(sq)]);
    projects = ps.docs.map(d => ({ id: d.id, ...d.data() }));
    storeItems = ss.docs.map(d => ({ id: d.id, ...d.data() }));
    renderPublic('projects');
    renderPublic('store');
  } catch(e) {
    document.getElementById('projectsGrid').innerHTML = '<div style="grid-column:1/-1;text-align:center;color:#888;padding:2rem">تعذر التحميل</div>';
    document.getElementById('storeGrid').innerHTML = '<div style="grid-column:1/-1;text-align:center;color:#888;padding:2rem">تعذر التحميل</div>';
  }
}

// ── RENDER PUBLIC ──
function renderPublic(type) {
  const grid = document.getElementById(type === 'projects' ? 'projectsGrid' : 'storeGrid');
  const items = type === 'projects' ? projects : storeItems;
  const f = currentFilter[type];
  const filtered = f === 'all' ? items : items.filter(i => i.category === f);
  if (!filtered.length) { grid.innerHTML = '<div class="empty-state"><div class="ei">📭</div><p>لا توجد عناصر بعد</p></div>'; return; }
  grid.innerHTML = filtered.map(p => `
    <div class="product-card" onclick="openModal('${p.id}','${type}')">
      <div class="card-thumb" style="background:${catGrad(p.category)}">
        ${p.imageUrl ? `<img src="${p.imageUrl}" alt="">` : `<span>${p.emoji||'📦'}</span>`}
      </div>
      <div class="card-body">
        <span class="card-tag">${catLabel(p.category)}</span>
        ${p.fileUrl ? '<span class="card-tag">قابل للتحميل</span>' : ''}
        <div class="card-title">${p.title||''}</div>
        <div class="card-desc">${p.description||''}</div>
        <div class="card-footer">
          <div class="card-price">${p.price||''}</div>
          <button class="card-btn">تفاصيل</button>
        </div>
      </div>
    </div>
  `).join('');
}

window._bridge.filterProducts = window.filterProducts = (cat, btn, type) => {
  currentFilter[type] = cat;
  const grid = type === 'projects' ? 'projectsGrid' : 'storeGrid';
  btn.closest('.filter-bar').querySelectorAll('.filter-btn').forEach(b => b.classList.remove('active'));
  btn.classList.add('active');
  renderPublic(type);
};

window._bridge.openModal = window.openModal = (id, type) => {
  const items = type === 'projects' ? projects : storeItems;
  const p = items.find(x => x.id === id);
  if (!p) return;
  const wa = p.whatsapp || '201227016225';
  const gallery = (p.gallery && p.gallery.length) ? p.gallery : (p.imageUrl ? [p.imageUrl] : []);
  const files = (p.files && p.files.length) ? p.files : (p.fileUrl ? [{url: p.fileUrl, name: 'تحميل'}] : []);
  let mediaHtml = '';
  if (gallery.length) {
    mediaHtml = `<div class="modal-gallery-main" id="modalGalleryMain"></div>`;
    if (gallery.length > 1) {
      mediaHtml += `<div class="modal-gallery-thumbs">${gallery.map((u,i)=>`<div class="mg-thumb" data-i="${i}" onclick="setModalGalleryItem(${i})">${/\.(mp4|webm|mov|ogg)(\?|$)/i.test(u)||u.includes('/video/') ? `<video src="${u}"></video><span class='mg-play'>▶</span>` : `<img src="${u}">`}</div>`).join('')}</div>`;
    }
  } else {
    mediaHtml = `<div class="modal-icon">${p.emoji||'📦'}</div>`;
  }
  document.getElementById('modalBody').innerHTML = `
    ${mediaHtml}
    <div class="modal-title">${p.title||''}</div>
    <div class="modal-price">${p.price||''}</div>
    ${p.description ? `<div class="modal-desc">${p.description}</div>` : ''}
    ${(p.features||[]).length ? `<div class="features-title">المميزات</div><ul class="features-list">${(p.features||[]).map(f=>`<li>${f}</li>`).join('')}</ul>` : ''}
    <div class="modal-btns">
      <a href="https://wa.me/${wa}?text=${encodeURIComponent('أهلاً، أنا مهتم بـ '+(p.title||''))}" class="btn-wa" target="_blank">💬 واتساب</a>
    </div>
    ${files.length ? `<div class="modal-files-list">${files.map(f=>`<button onclick="openActivation('${f.url}','${encodeURIComponent(f.name||'تحميل')}','${p.downloadCode||''}')" class="btn-dl modal-file-item">⬇️ ${f.name||'تحميل'}</button>`).join('')}</div>` : ''}
  `;
  window._modalGallery = gallery;
  if (gallery.length) setModalGalleryItem(0);
  document.getElementById('modalOverlay').classList.add('open');
};

window._bridge.setModalGalleryItem = window.setModalGalleryItem = (i) => {
  const gallery = window._modalGallery || [];
  const url = gallery[i];
  if (!url) return;
  const isVideo = /\.(mp4|webm|mov|ogg)(\?|$)/i.test(url) || url.includes('/video/');
  const main = document.getElementById('modalGalleryMain');
  if (main) main.innerHTML = isVideo
    ? `<video src="${url}" controls style="width:100%;border-radius:12px;margin-bottom:0.8rem;max-height:340px"></video>`
    : `<img src="${url}" style="width:100%;border-radius:12px;margin-bottom:0.8rem;max-height:340px;object-fit:cover">`;
  document.querySelectorAll('.mg-thumb').forEach((el,idx) => el.classList.toggle('active', idx === i));
};

window._bridge.closeModal = window.closeModal = (e) => {
  if (!e || e.target === document.getElementById('modalOverlay'))
    document.getElementById('modalOverlay').classList.remove('open');
};

// ── RENDER ADMIN ──
function renderAdminList(type) {
  const items = type === 'projects' ? projects : storeItems;
  const listEl = document.getElementById(type === 'projects' ? 'adminProjList' : 'adminStoreList');
  const countEl = document.getElementById(type === 'projects' ? 'projCount' : 'storeCount');
  if (countEl) countEl.textContent = items.length + ' عنصر';
  listEl.innerHTML = items.length ? items.map(p => `
    <div class="admin-item">
      <div class="admin-thumb">${p.imageUrl ? `<img src="${p.imageUrl}">` : (p.emoji||'📦')}</div>
      <div class="admin-info">
        <div class="ai-title">${p.title||'بدون اسم'}</div>
        <div class="ai-sub">${p.price||''} · ${catLabel(p.category)}</div>
      </div>
      <div class="admin-actions">
        <button class="a-icon-btn edit" onclick="editItem('${p.id}','${type}')">✏️</button>
        <button class="a-icon-btn del" onclick="deleteItem('${p.id}','${type}')">🗑️</button>
      </div>
    </div>
  `).join('') : '<p style="color:rgba(255,255,255,0.3);text-align:center;padding:2rem">لا توجد عناصر</p>';
}

// ── SAVE ──
window.saveProduct = async () => {
  const id = document.getElementById('editId').value;
  const section = document.getElementById('editSection').value || currentAdminSection;
  const title = document.getElementById('fTitle').value.trim();
  const price = document.getElementById('fPrice').value.trim();
  if (!title || !price) { showToast('الاسم والسعر مطلوبان', true); return; }
  const features = [...document.querySelectorAll('#featWrap .feature-row input')].map(i=>i.value.trim()).filter(Boolean);
  const data = {
    title, description: document.getElementById('fDesc').value.trim(),
    price, category: document.getElementById('fCat').value,
    emoji: document.getElementById('fEmoji').value.trim(),
    features, whatsapp: document.getElementById('fWa').value.trim(),
    gallery: galleryUrls, imageUrl: galleryUrls[0] || '', files: fileUrls, fileUrl: fileUrls[0]?.url || '', downloadCode: document.getElementById('fCode').value.trim().toUpperCase(), updatedAt: serverTimestamp()
  };
  const col = section === 'projects' ? 'projects' : 'store';
  try {
    if (id) { await updateDoc(doc(db, col, id), data); showToast('✅ تم التعديل'); }
    else { data.createdAt = serverTimestamp(); await addDoc(collection(db, col), data); showToast('✅ تم الإضافة'); }
    resetForm(); loadCollection(col);
  } catch(e) { showToast('خطأ: ' + e.message, true); }
};

window._bridge.editItem = window.editItem = (id, type) => {
  const items = type === 'projects' ? projects : storeItems;
  const p = items.find(x => x.id === id);
  if (!p) return;
  document.getElementById('formTitle').textContent = '✏️ تعديل';
  document.getElementById('editId').value = id;
  document.getElementById('editSection').value = type;
  document.getElementById('fTitle').value = p.title||'';
  document.getElementById('fDesc').value = p.description||'';
  document.getElementById('fPrice').value = p.price||'';
  document.getElementById('fCat').value = p.category||'other';
  document.getElementById('fEmoji').value = p.emoji||'';
  document.getElementById('fWa').value = p.whatsapp||'201227016225';
  document.getElementById('fCode').value = p.downloadCode||'';
  galleryUrls = p.gallery && p.gallery.length ? [...p.gallery] : (p.imageUrl ? [p.imageUrl] : []);
  fileUrls = p.files && p.files.length ? [...p.files] : (p.fileUrl ? [{url: p.fileUrl, name: 'ملف'}] : []);
  renderGalleryPreviews();
  renderFilePreviews();
  const countEl = document.getElementById('galCount');
  if (countEl) countEl.textContent = galleryUrls.length ? `(${galleryUrls.length} ملف)` : '';
  const fileCountEl = document.getElementById('fileCount');
  if (fileCountEl) fileCountEl.textContent = fileUrls.length ? `(${fileUrls.length} ملف)` : '';
  document.getElementById('imgTxt').textContent = galleryUrls.length ? `✅ ${galleryUrls.length} ملف موجود` : 'اضغط لرفع صور / فيديوهات (يمكن اختيار أكثر من ملف)';
  document.getElementById('fileTxt').textContent = fileUrls.length ? `✅ ${fileUrls.length} ملف موجود` : 'اضغط لرفع ملف أو أكثر (مشروع متكامل)';
  const fw = document.getElementById('featWrap');
  fw.innerHTML = (p.features||[]).map(f=>`<div class="feature-row"><input type="text" value="${f}"><button onclick="this.parentElement.remove()">✕</button></div>`).join('');
  document.querySelector('.admin-card').scrollIntoView({ behavior: 'smooth' });
};

window.deleteItem = async (id, type) => {
  if (!confirm('هل أنت متأكد؟')) return;
  const col = type === 'projects' ? 'projects' : 'store';
  try { await deleteDoc(doc(db, col, id)); showToast('🗑️ تم الحذف'); loadCollection(col); }
  catch(e) { showToast('خطأ في الحذف', true); }
};

window._bridge.resetForm = window.resetForm = () => {
  document.getElementById('formTitle').textContent = '➕ إضافة';
  ['editId','editSection','fTitle','fDesc','fPrice','fEmoji'].forEach(id => document.getElementById(id).value = '');
  document.getElementById('fCat').value = currentAdminSection === 'projects' ? 'medical' : 'satellite';
  document.getElementById('fWa').value = '201227016225';
  document.getElementById('fCode').value = '';
  document.getElementById('fImg').value = '';
  document.getElementById('fFile').value = '';
  const wrap = document.getElementById('galPreviewWrap');
  if (wrap) wrap.innerHTML = '';
  const fileWrap = document.getElementById('filePreviewWrap');
  if (fileWrap) fileWrap.innerHTML = '';
  const countEl = document.getElementById('galCount');
  if (countEl) countEl.textContent = '';
  const fileCountEl = document.getElementById('fileCount');
  if (fileCountEl) fileCountEl.textContent = '';
  document.getElementById('imgTxt').textContent = 'اضغط لرفع صور / فيديوهات (يمكن اختيار أكثر من ملف)';
  document.getElementById('fileTxt').textContent = 'اضغط لرفع ملف أو أكثر (مشروع متكامل)';
  document.getElementById('featWrap').innerHTML = '<div class="feature-row"><input type="text" placeholder="ميزة..."><button onclick="this.parentElement.remove()">✕</button></div>';
  galleryUrls = []; fileUrls = [];
};

window._bridge.addFeat = window.addFeat = () => {
  const fw = document.getElementById('featWrap');
  const row = document.createElement('div'); row.className = 'feature-row';
  row.innerHTML = '<input type="text" placeholder="ميزة..."><button onclick="this.parentElement.remove()">✕</button>';
  fw.appendChild(row);
};

// ── CLOUDINARY ──
function cloudUpload(file, progBg, progFill, txtEl) {
  return new Promise((resolve, reject) => {
    const fd = new FormData();
    fd.append('file', file);
    fd.append('upload_preset', PRESET);
    const xhr = new XMLHttpRequest();
    document.getElementById(progBg).style.display = 'block';
    xhr.upload.onprogress = e => {
      if (e.lengthComputable) {
        document.getElementById(progFill).style.width = Math.round(e.loaded/e.total*100) + '%';
        txtEl.textContent = 'جاري الرفع...';
      }
    };
    xhr.onload = () => {
      document.getElementById(progBg).style.display = 'none';
      xhr.status < 300 ? resolve(JSON.parse(xhr.responseText).secure_url) : reject(new Error('فشل'));
    };
    xhr.onerror = () => { document.getElementById(progBg).style.display = 'none'; reject(); };
    xhr.open('POST', `https://api.cloudinary.com/v1_1/${CLOUD}/auto/upload`);
    xhr.send(fd);
  });
}

window.handleImg = async (input) => {
  const files = [...input.files];
  if (!files.length) return;
  const txt = document.getElementById('imgTxt');
  const countEl = document.getElementById('galCount');
  let done = 0;
  txt.textContent = `جاري رفع ${files.length} ملف...`;
  for (const f of files) {
    try {
      const url = await cloudUpload(f, 'imgProg', 'imgProgFill', txt);
      galleryUrls.push(url);
      done++;
      txt.textContent = `جاري الرفع... (${done}/${files.length})`;
      addGalleryPreview(url, f.type.startsWith('video/'));
    } catch {
      txt.textContent = `❌ فشل رفع ملف رقم ${done + 1}`;
    }
  }
  txt.textContent = `✅ تم رفع ${galleryUrls.length} ملف`;
  if (countEl) countEl.textContent = `(${galleryUrls.length} ملف)`;
  input.value = '';
};

function addGalleryPreview(url, isVideo) {
  const wrap = document.getElementById('galPreviewWrap');
  if (!wrap) return;
  const box = document.createElement('div');
  box.style = 'position:relative;width:70px;height:70px;border-radius:8px;overflow:hidden;flex-shrink:0';
  box.innerHTML = isVideo
    ? `<video src="${url}" style="width:100%;height:100%;object-fit:cover"></video>`
    : `<img src="${url}" style="width:100%;height:100%;object-fit:cover">`;
  const rm = document.createElement('button');
  rm.textContent = '✕';
  rm.style = 'position:absolute;top:2px;left:2px;background:rgba(239,68,68,0.9);color:#fff;border:none;border-radius:50%;width:20px;height:20px;font-size:0.7rem;cursor:pointer;line-height:1';
  rm.onclick = () => {
    galleryUrls = galleryUrls.filter(u => u !== url);
    box.remove();
    const countEl = document.getElementById('galCount');
    if (countEl) countEl.textContent = galleryUrls.length ? `(${galleryUrls.length} ملف)` : '';
  };
  box.appendChild(rm);
  wrap.appendChild(box);
}

function renderGalleryPreviews() {
  const wrap = document.getElementById('galPreviewWrap');
  if (!wrap) return;
  wrap.innerHTML = '';
  galleryUrls.forEach(url => {
    const isVideo = /\.(mp4|webm|mov|ogg)(\?|$)/i.test(url) || url.includes('/video/');
    addGalleryPreview(url, isVideo);
  });
}

window.handleFile = async (input) => {
  const files = [...input.files];
  if (!files.length) return;
  const txt = document.getElementById('fileTxt');
  const countEl = document.getElementById('fileCount');
  let done = 0;
  txt.textContent = `جاري رفع ${files.length} ملف...`;
  for (const f of files) {
    try {
      const url = await cloudUpload(f, 'fileProg', 'fileProgFill', txt);
      fileUrls.push({ url, name: f.name });
      done++;
      txt.textContent = `جاري الرفع... (${done}/${files.length})`;
      addFilePreview(url, f.name);
    } catch {
      txt.textContent = `❌ فشل رفع ملف رقم ${done + 1}`;
    }
  }
  txt.textContent = `✅ تم رفع ${fileUrls.length} ملف`;
  if (countEl) countEl.textContent = `(${fileUrls.length} ملف)`;
  input.value = '';
};

function addFilePreview(url, name) {
  const wrap = document.getElementById('filePreviewWrap');
  if (!wrap) return;
  const row = document.createElement('div');
  row.style = 'display:flex;align-items:center;gap:0.5rem;background:rgba(255,255,255,0.05);border-radius:7px;padding:0.4rem 0.7rem;font-size:0.8rem;color:rgba(255,255,255,0.7)';
  row.innerHTML = `<span style="flex:1;overflow:hidden;text-overflow:ellipsis;white-space:nowrap">📄 ${name}</span>`;
  const rm = document.createElement('button');
  rm.textContent = '✕';
  rm.style = 'background:rgba(239,68,68,0.2);border:none;border-radius:5px;color:#ef4444;padding:0.2rem 0.5rem;cursor:pointer;flex-shrink:0';
  rm.onclick = () => {
    fileUrls = fileUrls.filter(f => f.url !== url);
    row.remove();
    const countEl = document.getElementById('fileCount');
    if (countEl) countEl.textContent = fileUrls.length ? `(${fileUrls.length} ملف)` : '';
  };
  row.appendChild(rm);
  wrap.appendChild(row);
}

function renderFilePreviews() {
  const wrap = document.getElementById('filePreviewWrap');
  if (!wrap) return;
  wrap.innerHTML = '';
  fileUrls.forEach(f => addFilePreview(f.url, f.name));
}

// ── HELPERS ──
function catGrad(c) { return {medical:'linear-gradient(135deg,#0f1f0f,#1e4d1e)',church:'linear-gradient(135deg,#1a0f28,#3d1f6b)',business:'linear-gradient(135deg,#101828,#1e3a5f)',satellite:'linear-gradient(135deg,#0a1628,#1a3a6b)',electronics:'linear-gradient(135deg,#1a1a1a,#3a3a3a)',accessories:'linear-gradient(135deg,#2a1a0a,#5a3a1a)',other:'linear-gradient(135deg,#1a1a1a,#3a3a3a)'}[c]||'linear-gradient(135deg,#1a1a1a,#3a3a3a)'; }
function catLabel(c) { return {medical:'طب',church:'كنيسة',business:'أعمال',satellite:'فضائيات',electronics:'إلكترونيات',accessories:'إكسسوارات',other:'أخرى'}[c]||'أخرى'; }

let toastT;
window._bridge.showToast = window.showToast = (msg, err=false) => {
  const t = document.getElementById('toast');
  t.textContent = msg; t.className = 'toast'+(err?' error':'')+' show';
  clearTimeout(toastT); toastT = setTimeout(()=>t.classList.remove('show'),3000);
};


// ── MEDIA ──
let mediaItems = [];
let mediaFilter = 'all';
let mFileUrl = '', mThumbUrl = '', mEditId = '';

async function loadMedia() {
  try {
    const q = query(collection(db, 'media'), orderBy('createdAt', 'desc'));
    const snap = await getDocs(q);
    mediaItems = snap.docs.map(d => ({ id: d.id, ...d.data() }));
    renderMedia();
    renderAdminMedia();
  } catch(e) {}
}

function renderMedia() {
  const grid = document.getElementById('mediaGrid');
  if (!grid) return;
  const filtered = mediaFilter === 'all' ? mediaItems : mediaItems.filter(i => i.mediaType === mediaFilter);
  if (!filtered.length) { grid.innerHTML = '<div class="empty-state"><div class="ei">🎬</div><p>لا توجد وسائط بعد</p></div>'; return; }
  grid.innerHTML = filtered.map(m => {
    const icon = {image:'🖼️',video:'🎬',audio:'🎵',other:'📁'}[m.mediaType]||'📁';
    const thumb = m.thumbUrl || m.fileUrl;
    return `<div class="product-card" onclick="openMediaModal('${m.id}')">
      <div class="card-thumb" style="background:linear-gradient(135deg,#1a1a2e,#16213e);position:relative">
        ${m.mediaType === 'image' && m.fileUrl ? `<img src="${m.fileUrl}" alt="">` : 
          m.thumbUrl ? `<img src="${m.thumbUrl}" alt="">` : `<span style="font-size:3rem">${icon}</span>`}
        ${m.mediaType === 'video' ? '<div style="position:absolute;bottom:8px;right:8px;background:rgba(0,0,0,0.7);color:#fff;border-radius:50%;width:32px;height:32px;display:flex;align-items:center;justify-content:center;font-size:0.9rem">▶</div>' : ''}
      </div>
      <div class="card-body">
        <span class="card-tag">${{image:'صورة',video:'فيديو',audio:'صوت',other:'ملف'}[m.mediaType]||'ملف'}</span>
        <div class="card-title">${m.title||''}</div>
        <div class="card-desc">${m.description||''}</div>
        <div class="card-footer">
          <div class="card-price"></div>
          <button class="card-btn">${m.mediaType === 'image' ? '🔍 عرض' : m.mediaType === 'video' ? '▶ مشاهدة' : m.mediaType === 'audio' ? '🎵 استماع' : '⬇️ تحميل'}</button>
        </div>
      </div>
    </div>`;
  }).join('');
}

window._bridge.filterMedia = window.filterMedia = (type, btn) => {
  mediaFilter = type;
  btn.closest('.filter-bar').querySelectorAll('.filter-btn').forEach(b => b.classList.remove('active'));
  btn.classList.add('active');
  renderMedia();
};

window._bridge.openMediaModal = window.openMediaModal = (id) => {
  const m = mediaItems.find(x => x.id === id);
  if (!m) return;
  let mediaEl = '';
  if (m.mediaType === 'image' && m.fileUrl) mediaEl = `<img src="${m.fileUrl}" style="width:100%;border-radius:12px;margin-bottom:1rem">`;
  else if (m.mediaType === 'video' && m.fileUrl) mediaEl = `<video src="${m.fileUrl}" controls style="width:100%;border-radius:12px;margin-bottom:1rem"></video>`;
  else if (m.mediaType === 'audio' && m.fileUrl) mediaEl = `<audio src="${m.fileUrl}" controls style="width:100%;margin-bottom:1rem"></audio>`;
  document.getElementById('modalBody').innerHTML = `
    ${mediaEl}
    <div class="modal-title">${m.title||''}</div>
    ${m.description ? `<div class="modal-desc">${m.description}</div>` : ''}
    ${m.fileUrl ? `<div class="modal-btns"><a href="${m.fileUrl}" target="_blank" class="btn-dl" style="flex:1">⬇️ تحميل</a></div>` : ''}
  `;
  document.getElementById('modalOverlay').classList.add('open');
};

function renderAdminMedia() {
  const list = document.getElementById('adminMediaList');
  const count = document.getElementById('mediaCount');
  if (!list) return;
  if (count) count.textContent = mediaItems.length + ' عنصر';
  list.innerHTML = mediaItems.length ? mediaItems.map(m => `
    <div class="admin-item">
      <div class="admin-thumb">${m.thumbUrl || (m.mediaType === 'image' && m.fileUrl) ? `<img src="${m.thumbUrl || m.fileUrl}">` : ({image:'🖼️',video:'🎬',audio:'🎵',other:'📁'}[m.mediaType]||'📁')}</div>
      <div class="admin-info">
        <div class="ai-title">${m.title||'بدون عنوان'}</div>
        <div class="ai-sub">${{image:'صورة',video:'فيديو',audio:'صوت',other:'ملف'}[m.mediaType]||'ملف'}</div>
      </div>
      <div class="admin-actions">
        <button class="a-icon-btn del" onclick="deleteMedia('${m.id}')">🗑️</button>
      </div>
    </div>
  `).join('') : '<p style="color:rgba(255,255,255,0.3);text-align:center;padding:2rem">لا توجد وسائط</p>';
}

window.handleMediaFile = async (input) => {
  if (!input.files[0]) return;
  const txt = document.getElementById('mFileTxt');
  const icon = document.getElementById('mUpIcon');
  const type = document.getElementById('mType').value;
  icon.textContent = {image:'🖼️',video:'🎬',audio:'🎵',other:'📁'}[type]||'📁';
  try {
    mFileUrl = await cloudUpload(input.files[0], 'mFileProg', 'mFileProgFill', txt);
    txt.textContent = '✅ ' + input.files[0].name;
  } catch { txt.textContent = '❌ فشل الرفع'; }
};

window.handleMediaThumb = async (input) => {
  if (!input.files[0]) return;
  const txt = document.getElementById('mThumbTxt');
  try {
    mThumbUrl = await cloudUpload(input.files[0], 'mThumbProg', 'mThumbProgFill', txt);
    txt.textContent = '✅ تم رفع الغلاف';
    const r = new FileReader(); r.onload = e => { document.getElementById('mThumbPrev').src = e.target.result; document.getElementById('mThumbPrev').style.display = 'block'; }; r.readAsDataURL(input.files[0]);
  } catch { txt.textContent = '❌ فشل'; }
};

window.saveMedia = async () => {
  const title = document.getElementById('mTitle').value.trim();
  if (!title) { showToast('العنوان مطلوب', true); return; }
  if (!mFileUrl) { showToast('ارفع ملف أولاً', true); return; }
  const data = {
    title, description: document.getElementById('mDesc').value.trim(),
    mediaType: document.getElementById('mType').value,
    fileUrl: mFileUrl, thumbUrl: mThumbUrl,
    createdAt: serverTimestamp()
  };
  try {
    await addDoc(collection(db, 'media'), data);
    showToast('✅ تم الإضافة');
    resetMediaForm();
    loadMedia();
  } catch(e) { showToast('خطأ: ' + e.message, true); }
};

window.deleteMedia = async (id) => {
  if (!confirm('هل أنت متأكد؟')) return;
  try { await deleteDoc(doc(db, 'media', id)); showToast('🗑️ تم الحذف'); loadMedia(); }
  catch(e) { showToast('خطأ', true); }
};

window._bridge.resetMediaForm = window.resetMediaForm = () => {
  document.getElementById('mTitle').value = '';
  document.getElementById('mDesc').value = '';
  document.getElementById('mType').value = 'image';
  document.getElementById('mFile').value = '';
  document.getElementById('mThumb').value = '';
  document.getElementById('mFileTxt').textContent = 'اضغط لرفع صورة / فيديو / صوت';
  document.getElementById('mThumbTxt').textContent = 'صورة غلاف (اختياري)';
  document.getElementById('mThumbPrev').style.display = 'none';
  mFileUrl = ''; mThumbUrl = ''; mEditId = '';
};

// ── ACTIVATION SYSTEM ──
let _activationFileUrl = '';
let _activationFileName = '';
let _activationCode = '';

window.openActivation = (fileUrl, fileName, projectCode) => {
  _activationFileUrl = fileUrl;
  _activationFileName = decodeURIComponent(fileName);
  _activationCode = projectCode;

  // لو مفيش كود، حمل مباشرة
  if (!projectCode) {
    const a = document.createElement('a');
    a.href = fileUrl;
    a.target = '_blank';
    a.click();
    return;
  }

  document.getElementById('activationCode').value = '';
  document.getElementById('activationError').style.display = 'none';
  const waText = encodeURIComponent('أهلاً، أريد الحصول على كود تفعيل التحميل');
  document.getElementById('activationWaBtn').href = `https://wa.me/201227016225?text=${waText}`;
  document.getElementById('activationModal').classList.add('open');
};

window.checkActivationCode = () => {
  const code = document.getElementById('activationCode').value.trim().toUpperCase();
  if (code === _activationCode) {
    document.getElementById('activationModal').classList.remove('open');
    const a = document.createElement('a');
    a.href = _activationFileUrl;
    a.target = '_blank';
    a.download = _activationFileName;
    a.click();
  } else {
    document.getElementById('activationError').style.display = 'block';
  }
};

window.closeActivation = () => {
  document.getElementById('activationModal').classList.remove('open');
};

loadPublicOnly();
loadMedia();
</script>
</body>
</html>
