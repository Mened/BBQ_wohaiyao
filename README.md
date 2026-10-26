<!DOCTYPE html>
<html lang="zh-CN">
<head>
<meta charset="UTF-8">
<title>Mened 的OC小屋</title>
<style>
body{background:#f8f5fc;color:#333;font-family:system-ui;padding:2em;}
h1{color:#9966bb;}
</style>
</head>
<body>
<h1>欢迎来到我的OC和插画主页✨</h1>
<p>这里放角色介绍、画作</p>
</body>
</html>
<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width,initial-scale=1">
<title>FxA House</title>
<style>
@keyframes float{0%,100%{transform:translateY(0)}50%{transform:translateY(-4px)}}
@keyframes wiggle{0%,100%{transform:rotate(0)}25%{transform:rotate(-3deg)}75%{transform:rotate(3deg)}}
@keyframes blink{0%,100%{opacity:1}50%{opacity:.4}}
@keyframes marquee{0%{transform:translateX(100%)}100%{transform:translateX(-100%)}}
@keyframes sparkle{0%,100%{opacity:1}50%{opacity:.4;transform:scale(.8)}}
@keyframes heartbeat{0%,100%{transform:scale(1)}50%{transform:scale(1.15)}}
@keyframes drift{0%{transform:translateY(0) rotate(0)}100%{transform:translateY(-20px) rotate(10deg);opacity:0}}

*{box-sizing:border-box;margin:0;padding:0}
body{
  background:#fef8ee;
  background-image:radial-gradient(#f0e0c8 1px,transparent 1px);
  background-size:24px 24px;
  color:#6a4a30;
  font-family:system-ui,"Segoe UI",sans-serif;
  min-height:100vh;
}

/* === 进站弹窗 === */
.warn{position:fixed;inset:0;z-index:9999;background:rgba(254,248,238,.92);display:flex;align-items:center;justify-content:center;padding:16px;backdrop-filter:blur(4px)}
.warn.gone{display:none}
.warn-box{width:92%;max-width:380px;background:#fff;border:3px solid #f0c8a0;border-radius:16px;padding:24px 20px;text-align:center;box-shadow:0 8px 24px rgba(180,140,100,.15)}
.warn-box h2{color:#e08860;font-size:16px;margin-bottom:12px}
.warn-box p{font-size:11px;line-height:1.8;color:#8a7060;margin-bottom:16px;text-align:left}
.warn-box button{padding:9px 28px;margin:4px;font-size:12px;font-weight:900;font-family:inherit;cursor:pointer;border-radius:20px;border:2.5px solid}
.btn-enter{background:#f0a870;color:#fff;border-color:#d89050}
.btn-enter:active{transform:scale(.97)}
.btn-leave{background:#f0e8e0;color:#a09080;border-color:#d8c8b8}

/* foxbun decorations in popup */
.warn-chars{display:flex;justify-content:center;gap:8px;margin-bottom:12px}
.mini-fox,.mini-bun{width:40px;height:36px;border-radius:50%;position:relative;display:inline-block}
.mini-fox{background:#ffe8a0;border:2px solid #c8a050}
.mini-fox::before,.mini-fox::after{content:"";position:absolute;top:-4px;border-left:5px solid transparent;border-right:5px solid transparent;border-bottom:8px solid #f0b040}
.mini-fox::before{left:4px}
.mini-fox::after{right:4px}
.mini-bun{background:#f0e8f4;border:2px solid #b8a0c0}
.mini-bun::before,.mini-bun::after{content:"";position:absolute;top:3px;width:9px;height:18px;background:#ece4f0;border:1.5px solid #b8a0c0;border-radius:50%}
.mini-bun::before{left:-5px}
.mini-bun::after{right:-5px}
.mf-face,.mb-face{position:absolute;top:40%;left:0;right:0;text-align:center;font-size:7px;font-weight:900;z-index:1}
.mf-face{color:#a06020}
.mb-face{color:#8070a0}

.page{max-width:720px;margin:0 auto;padding:10px}

/* === 顶部标题区 === */
.header{
  text-align:center;padding:20px 12px;
  background:#fff;border:3px solid #f0d0a0;border-radius:16px;
  margin-bottom:10px;position:relative;overflow:hidden;
  box-shadow:0 4px 12px rgba(200,160,100,.1);
}
.header::before{content:"";position:absolute;top:0;left:0;right:0;height:6px;background:linear-gradient(90deg,#f8d8a8,#f0a878,#f8b8c8,#c8d8f0,#b8e8d0,#f8d8a8)}
.title{font-size:22px;font-weight:900;color:#d08850;line-height:1.4}
.subtitle{font-size:10px;color:#b09878;margin-top:4px;letter-spacing:2px}
.header-deco{margin-top:8px;font-size:12px;color:#e0b888;letter-spacing:6px}
/* fox and bunny emoji in header */
.header-chars{font-size:28px;margin-top:6px;animation:float 3s ease-in-out infinite}

/* === 跑马灯 === */
.marquee-bar{overflow:hidden;background:#fff8f0;border:2px solid #f0d8b8;border-radius:10px;padding:5px 0;margin-bottom:10px}
.marquee-text{display:inline-block;white-space:nowrap;animation:marquee 20s linear infinite;font-size:11px;color:#c08850;font-weight:700}
.mq-star{color:#f0a060;animation:sparkle 1.5s infinite;display:inline-block}

/* === 导航 === */
.nav{display:flex;flex-wrap:wrap;justify-content:center;gap:5px;margin-bottom:10px}
.nav a{
  display:inline-flex;align-items:center;gap:4px;
  padding:7px 16px;
  background:#fff;border:2.5px solid #f0d0a8;border-radius:20px;
  color:#c08850;font-size:11px;font-weight:800;
  text-decoration:none;transition:all .15s;
  box-shadow:0 2px 0 #e8c8a0;
}
.nav a:hover{background:#fef0e0;border-color:#e0a870;transform:translateY(-2px);box-shadow:0 4px 0 #e8c8a0}
.nav a:active{transform:translateY(1px);box-shadow:none}
.nav-icon{font-size:14px;animation:float 2s ease-in-out infinite}

/* === 双栏 === */
.layout{display:flex;gap:10px;margin-bottom:10px}
.sidebar{width:175px;flex:none}
.main{flex:1;min-width:0}

/* === 通用盒子 - 奶油饼干风格 === */
.box{
  background:#fff;
  border:2.5px solid #f0d0a8;border-radius:12px;
  margin-bottom:10px;overflow:hidden;
  box-shadow:0 3px 8px rgba(200,160,100,.08);
}
.box-title{
  background:linear-gradient(90deg,#fef0d8,#fde8c8);
  padding:6px 10px;font-size:11px;font-weight:900;
  color:#c08040;display:flex;align-items:center;gap:5px;
  border-bottom:2px solid #f0d8b8;
}
.box-title-icon{font-size:14px;animation:wiggle 2s ease-in-out infinite}
.box-body{padding:10px;font-size:11px;line-height:1.75;color:#7a6050}

/* === 头像区 === */
.profile{text-align:center}
.avatar{
  width:100px;height:100px;margin:6px auto;
  border:3px solid #f0c8a0;border-radius:50%;
  background:#fef8ee;overflow:hidden;
  display:flex;align-items:center;justify-content:center;
  font-size:44px;box-shadow:0 3px 8px rgba(200,150,100,.15);
}
.avatar img{width:100%;height:100%;object-fit:cover;display:block}
.profile-name{font-size:14px;color:#d08850;font-weight:900;margin:6px 0 2px}
.profile-desc{font-size:9px;color:#a08868;line-height:1.6}
.status{font-size:10px;color:#70b880;margin-top:6px;font-weight:700}
.status-dot{display:inline-block;width:6px;height:6px;background:#70c880;border-radius:50%;margin-right:3px;animation:blink 1.5s infinite}

/* === 链接列表 === */
.links{list-style:none;padding:0}
.links li{padding:4px 6px;border-bottom:1.5px dashed #f0e0d0}
.links li::before{content:"*";color:#f0a060;margin-right:5px;font-weight:900}
.links a{color:#c08850;text-decoration:none;font-size:10px;font-weight:700}
.links a:hover{color:#e0a060;text-decoration:underline}

/* === 画廊 === */
.gallery-grid{display:grid;grid-template-columns:repeat(3,1fr);gap:6px}
.gallery-item{
  aspect-ratio:1;background:#fef8ee;
  border:2.5px solid #f0d8b8;border-radius:10px;
  display:flex;align-items:center;justify-content:center;
  font-size:28px;cursor:pointer;overflow:hidden;
  transition:all .15s;
}
.gallery-item:hover{border-color:#e0a870;transform:scale(1.04);box-shadow:0 4px 10px rgba(200,150,100,.15)}
.gallery-item img{width:100%;height:100%;object-fit:cover;display:block;border-radius:7px}

/* === 游戏卡片 === */
.game-card{
  display:flex;gap:10px;padding:8px;
  border:2px solid #f0d8c0;border-radius:10px;
  background:#fffcf5;margin-bottom:6px;
  cursor:pointer;transition:all .15s;text-decoration:none;color:inherit;
}
.game-card:hover{border-color:#e0a870;background:#fef4e8;transform:translateY(-2px);box-shadow:0 4px 8px rgba(200,150,100,.12)}
.game-icon{
  width:42px;height:42px;background:#fef0d8;
  border:2px solid #f0d0a8;border-radius:10px;
  display:flex;align-items:center;justify-content:center;
  font-size:20px;flex:none;overflow:hidden;
}
.game-icon img{width:100%;height:100%;object-fit:cover;border-radius:8px}
.game-info{min-width:0}
.game-name{font-size:11px;font-weight:900;color:#c08040}
.game-desc{font-size:9px;color:#a09078;margin-top:2px}

/* === 更新日志 === */
.update{padding:4px 0;font-size:10px;border-bottom:1.5px dashed #f0e0d0}
.update-date{color:#e0a060;font-weight:800;margin-right:6px}
.update-text{color:#907868}

/* === 角色介绍区 === */
.chara-row{display:flex;gap:8px;margin-bottom:8px}
.chara-card{
  flex:1;padding:10px;text-align:center;
  border:2px solid #f0d8c0;border-radius:10px;
  background:#fffcf5;
}
.chara-card:hover{border-color:#e0a870}
.chara-avatar{
  width:60px;height:60px;margin:0 auto 6px;
  border-radius:50%;overflow:hidden;
  display:flex;align-items:center;justify-content:center;
  font-size:30px;
}
.chara-avatar img{width:100%;height:100%;object-fit:cover}
.chara-fox .chara-avatar{background:#fff0c8;border:2.5px solid #e0b060}
.chara-bun .chara-avatar{background:#f0e8f8;border:2.5px solid #c0a8d0}
.chara-name{font-size:12px;font-weight:900;margin-bottom:2px}
.chara-fox .chara-name{color:#c88030}
.chara-bun .chara-name{color:#9878b0}
.chara-tag{font-size:8px;color:#a09080;line-height:1.5}

/* === 留言板 === */
.gb-entry{padding:6px;border-bottom:1.5px dashed #f0e0d0;font-size:10px}
.gb-name{color:#e08860;font-weight:900}
.gb-date{color:#c0b0a0;font-size:8px;margin-left:4px}
.gb-msg{color:#8a7a68;margin-top:2px}

/* === 计数器 === */
.counter{text-align:center;padding:10px;font-size:10px;color:#c0a888}
.counter-num{
  display:inline-block;padding:2px 5px;
  background:#fef0d8;border:2px solid #f0d0a8;border-radius:4px;
  color:#c08040;font-weight:900;font-size:13px;
  margin:0 1px;font-family:monospace;
}

/* === 页脚 === */
.footer{
  text-align:center;padding:14px;
  font-size:9px;color:#b8a898;
  border-top:2px dashed #f0e0d0;margin-top:10px;
}
.footer-deco{font-size:20px;margin-bottom:6px}

/* === 装饰效果 === */
.spark{display:inline-block;animation:sparkle 1.5s infinite;color:#f0a060}
.float{display:inline-block;animation:float 2s ease-in-out infinite}
.heartbeat{display:inline-block;animation:heartbeat 1s infinite;color:#f08888}
.wiggle{display:inline-block;animation:wiggle 2s ease-in-out infinite}

/* === 施工中 === */
.wip{
  text-align:center;padding:8px;
  background:repeating-linear-gradient(45deg,#fef8ee,#fef8ee 8px,#fef0d8 8px,#fef0d8 16px);
  border:2px solid #f0d0a0;border-radius:10px;
  color:#d09860;font-size:10px;font-weight:900;
  margin-bottom:10px;
}

/* 浮动小图标装饰 */
.float-deco{
  position:fixed;pointer-events:none;z-index:0;
  font-size:16px;opacity:.15;
}

/* 鼠标星星 */
.trail{position:fixed;pointer-events:none;z-index:9998;font-size:12px;animation:drift .8s ease-out forwards}

/* 手机适配 */
@media(max-width:600px){
  .layout{flex-direction:column}
  .sidebar{width:100%}
  .gallery-grid{grid-template-columns:repeat(2,1fr)}
  .chara-row{flex-direction:column}
  .nav a{padding:6px 12px;font-size:10px}
}
</style>
</head>
<body>

<!-- ====== 进站弹窗 ====== -->
<div class="warn" id="warn">
<div class="warn-box">
<div class="warn-chars">
<div class="mini-fox"><div class="mf-face">&gt;w&lt;</div></div>
<span style="color:#f0a080;font-size:16px;align-self:center;animation:heartbeat 1s infinite">&#9829;</span>
<div class="mini-bun"><div class="mb-face">-w-</div></div>
</div>
<h2>&#127825; Welcome! &#127825;</h2>
<p>
&#9829; 本站包含原创角色的创作内容<br>
&#9829; 含CP向内容 (费得 x 小a)<br>
&#9829; 站内所有内容禁止无授权转载<br>
&#9829; 如果不适应以上内容请离开<br><br>
<span style="color:#e08860">确认以上内容后方可继续浏览~</span>
</p>
<button class="btn-enter" onclick="document.getElementById('warn').className='warn gone'">&#127825; 进入小屋</button>
<button class="btn-leave" onclick="history.back()">离开</button>
</div>
</div>

<div class="page">

<!-- ====== 顶部标题 ====== -->
<div class="header">
<div class="header-chars"><span class="wiggle">&#128049;</span> &#9829; <span class="wiggle">&#128048;</span></div>
<div class="title">&#127825; 费得与小a的小屋 &#127825;</div>
<div class="subtitle">fox x bunny creative house</div>
<div class="header-deco"><span class="spark">&#10047;</span> <span class="spark">&#10047;</span> <span class="spark">&#10047;</span></div>
</div>

<!-- 跑马灯 -->
<div class="marquee-bar">
<div class="marquee-text">
<span class="mq-star">&#10047;</span> Welcome to FxA House!
<span class="mq-star">&#10047;</span> 欢迎来到费得与小a的创作小屋!
<span class="mq-star">&#10047;</span> 禁止无授权转载!
<span class="mq-star">&#10047;</span> LOVE YOU~
<span class="mq-star">&#10047;</span>
</div>
</div>

<!-- 导航 -->
<div class="nav">
<a href="index.html"><span class="nav-icon">&#127968;</span> HOME</a>
<a href="gallery.html"><span class="nav-icon">&#127912;</span> GALLERY</a>
<a href="games.html"><span class="nav-icon">&#127918;</span> GAMES</a>
<a href="about.html"><span class="nav-icon">&#128049;</span> ABOUT</a>
<a href="links.html"><span class="nav-icon">&#128279;</span> LINKS</a>
</div>

<!-- ====== 双栏 ====== -->
<div class="layout">

<!-- 左栏 -->
<div class="sidebar">

<!-- 头像 -->
<div class="box">
<div class="box-title"><span class="box-title-icon">&#128049;</span> PROFILE</div>
<div class="box-body profile">
<!--
  ★ 换头像: 上传图片到 img/avatar.jpg 然后把下面emoji换成:
  <img src="img/avatar.jpg">
-->
<div class="avatar">&#127912;</div>
<div class="profile-name">&#10047; 站主名字</div>
<div class="profile-desc">
画画 / 游戏 / 费得厨<br>
&#128049;&#9829;&#128048;
</div>
<div class="status"><span class="status-dot"></span>online~</div>
</div>
</div>

<!-- 更新日志 -->
<div class="box">
<div class="box-title"><span class="box-title-icon">&#128196;</span> UPDATES</div>
<div class="box-body">
<!-- 新的加在最上面 -->
<div class="update"><span class="update-date">10/26</span><span class="update-text">小屋开张啦!</span></div>
<div class="update"><span class="update-date">10/26</span><span class="update-text">上传了新图~</span></div>
<div class="update"><span class="update-date">10/26</span><span class="update-text">游戏页施工中</span></div>
</div>
</div>

<!-- 链接 -->
<div class="box">
<div class="box-title"><span class="box-title-icon">&#128279;</span> LINKS</div>
<div class="box-body">
<!-- 改 href="#" 为你的链接地址 -->
<ul class="links">
<li><a href="#">Weibo</a></li>
<li><a href="#">Pixiv</a></li>
<li><a href="#">Lofter</a></li>
<li><a href="#">itch.io</a></li>
</ul>
</div>
</div>

<!-- 装饰盒子 -->
<div class="box">
<div class="box-title"><span class="box-title-icon">&#127925;</span> MOOD</div>
<div class="box-body" style="text-align:center;font-size:10px;color:#c0a080">
<span class="float" style="font-size:22px">&#128049;</span><br>
"非人~~~别惹我"<br>
<span style="font-size:8px;color:#d0b898">-- 费得, 每天</span>
</div>
</div>

</div>

<!-- ====== 右栏 ====== -->
<div class="main">

<!-- 欢迎 -->
<div class="box">
<div class="box-title"><span class="box-title-icon">&#127825;</span> WELCOME!</div>
<div class="box-body">
<!--
  ★ 加横幅大图: 在这段话上面加:
  <img src="img/banner.jpg" style="width:100%;border-radius:8px;margin-bottom:10px">
-->
<span class="spark">&#10047;</span> 欢迎来到费得与小a的创作小屋!<br><br>

这里存放着关于 <span style="color:#d08840;font-weight:900">费得</span> 和 <span style="color:#9878b0;font-weight:900">小a</span> 的所有创作~<br>
插画 / 小游戏 / 角色设定 / 世界观<br><br>

<span style="color:#f08888;font-weight:700">LOVE YOU~ &#9829;</span><br>
<span style="color:#d09060;font-weight:700">听话就给你棒棒糖 &#127853;</span><br><br>

<span style="color:#e08860;font-weight:900">NOTICE:</span> 站内所有内容为个人原创，<span style="color:#d06040">禁止无授权转载</span>
</div>
</div>

<!-- 角色介绍 -->
<div class="box">
<div class="box-title"><span class="box-title-icon">&#9829;</span> CHARACTERS</div>
<div class="box-body">
<!--
  ★ 插入角色立绘: 把 chara-avatar 里的 emoji 换成:
  <img src="img/feide.jpg">
-->
<div class="chara-row">
<div class="chara-card chara-fox">
<div class="chara-avatar">&#128049;</div>
<div class="chara-name">&#127825; 费得 / F-kun</div>
<div class="chara-tag">
+tsundere BOY<br>
傲娇小狐狸 / 嘴硬心软<br>
非人~~~别惹我<br>
(其实超级纯情)
</div>
</div>
<div class="chara-card chara-bun">
<div class="chara-avatar">&#128048;</div>
<div class="chara-name">&#127800; 小a / A-chan</div>
<div class="chara-tag">
+air-headed Girl<br>
天然呆垂耳兔 / 迷糊善良<br>
LOVE YOU~<br>
(费得的专属治愈)
</div>
</div>
</div>
<div style="text-align:center;font-size:10px;color:#d0a888">
&#128049; <span class="heartbeat">&#9829;</span> &#128048;<br>
<span style="font-size:8px">SUKI ~ &#10132; / &#10130; ~ SUKI</span>
</div>
</div>
</div>

<!-- 画廊 -->
<div class="box">
<div class="box-title"><span class="box-title-icon">&#127912;</span> GALLERY</div>
<div class="box-body">
<!--
  ★ 换画廊图片:
  把 <div class="gallery-item">里的emoji换成:
  <div class="gallery-item"><img src="img/art1.jpg"></div>
  
  想加更多图就复制更多 gallery-item
  想变2列: CSS里把 repeat(3 改成 repeat(2
-->
<div class="gallery-grid">
<div class="gallery-item">&#127912;</div>
<div class="gallery-item">&#127912;</div>
<div class="gallery-item">&#127912;</div>
<div class="gallery-item">&#127912;</div>
<div class="gallery-item">&#127912;</div>
<div class="gallery-item">&#127912;</div>
</div>
<div style="text-align:right;margin-top:6px">
<a href="gallery.html" style="color:#c08850;font-size:10px;text-decoration:none;font-weight:700">>> view all~</a>
</div>
</div>
</div>

<!-- 游戏 -->
<div class="box">
<div class="box-title"><span class="box-title-icon">&#127918;</span> GAMES</div>
<div class="box-body">
<!--
  ★ 给游戏加链接:
  把 <div class="game-card"> 改成:
  <a href="游戏地址" class="game-card" target="_blank">
  结尾 </div> 改成 </a>
  
  ★ 换游戏图标:
  把 game-icon 里emoji换成:
  <img src="img/game1.jpg">
-->

<div class="game-card">
<div class="game-icon">&#127856;</div>
<div class="game-info">
<div class="game-name">&#127856; 费得与小a的甜品工坊</div>
<div class="game-desc">换装+做蛋糕经营游戏!</div>
</div>
</div>

<div class="game-card">
<div class="game-icon">&#127769;</div>
<div class="game-info">
<div class="game-name">&#127769; 费得的偷心大作战</div>
<div class="game-desc">月下心跳距离游戏~</div>
</div>
</div>

<div class="game-card">
<div class="game-icon">&#127800;</div>
<div class="game-info">
<div class="game-name">&#127800; 费得与小a的秘密花园</div>
<div class="game-desc">花田收集甜蜜冒险!</div>
</div>
</div>

<div class="game-card">
<div class="game-icon">&#128165;</div>
<div class="game-info">
<div class="game-name">&#128165; 费得的节奏黑客</div>
<div class="game-desc">赛博风节奏音游!</div>
</div>
</div>

<div class="game-card">
<div class="game-icon">&#128293;</div>
<div class="game-info">
<div class="game-name">&#128293; 费得的秘密任务</div>
<div class="game-desc">给小a偷偷采花跑酷!</div>
</div>
</div>

<div class="game-card">
<div class="game-icon">&#128151;</div>
<div class="game-info">
<div class="game-name">&#128151; 育儿日记</div>
<div class="game-desc">照顾狐兔混血宝宝!</div>
</div>
</div>

<div style="text-align:right;margin-top:6px">
<a href="games.html" style="color:#c08850;font-size:10px;text-decoration:none;font-weight:700">>> play all games~</a>
</div>
</div>
</div>

<!-- 留言板 -->
<div class="box">
<div class="box-title"><span class="box-title-icon">&#128172;</span> GUESTBOOK</div>
<div class="box-body">
<div class="gb-entry">
<span class="gb-name">&#128049; Admin</span><span class="gb-date">10/26</span>
<div class="gb-msg">Welcome~ 有什么想说的通过社交媒体告诉我!</div>
</div>
<div class="gb-entry">
<span class="gb-name">&#128048; ...</span><span class="gb-date">??/??</span>
<div class="gb-msg">等待第一位访客... <span class="spark">&#10047;</span></div>
</div>
</div>
</div>

<!-- 施工中 -->
<div class="wip">
&#128679; UNDER CONSTRUCTION ~ 还在慢慢建设中 ~ &#128679;
</div>

</div>
</div>

<!-- 计数器 -->
<div class="counter">
&#128049; visitor count &#128048;<br>
<span class="counter-num">0</span>
<span class="counter-num">0</span>
<span class="counter-num">1</span>
<span class="counter-num">4</span>
<span class="counter-num">2</span>
<span class="counter-num">8</span>
</div>

<!-- 页脚 -->
<div class="footer">
<div class="footer-deco">&#128049; <span class="heartbeat">&#9829;</span> &#128048;</div>
(c) 2026 FxA House - All Rights Reserved<br>
do not repost without permission<br>
<span style="color:#d0c0b0">made with &#9829; and too many sweets</span>
</div>

</div>

<!-- 鼠标跟随特效 -->
<script>
document.addEventListener("mousemove",function(e){
if(Math.random()>.7)return;
var s=["&#10047;","&#9829;","*","+","&#10045;"];
var c=["#f0a060","#f08888","#c8a0d0","#88c8a0","#e0b878"];
var el=document.createElement("div");
el.className="trail";
el.innerHTML=s[Math.floor(Math.random()*s.length)];
el.style.left=e.pageX+"px";
el.style.top=e.pageY+"px";
el.style.color=c[Math.floor(Math.random()*c.length)];
document.body.appendChild(el);
setTimeout(function(){if(el.parentNode)el.parentNode.removeChild(el);},800);
});
</script>

</body>
</html>
