<!DOCTYPE html>
<html lang="zh-CN">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>杨掌柜大学生专属名片</title>
<style>
*{box-sizing:border-box;font-family:"Microsoft YaHei",sans-serif;margin:0;padding:0}
body{background:#f5f7fa;padding:20px;display:flex;justify-content:center;align-items:center;min-height:100vh}
.main{width:100%;max-width:420px;background:#ffffff;border-radius:12px;box-shadow:0 2px 12px rgba(0,0,0,0.08);padding:30px}
.title{font-size:20px;font-weight:600;color:#1f2937;text-align:center;margin-bottom:6px}
.subtitle{font-size:14px;color:#6b7280;text-align:center;margin-bottom:24px}
.input-box{width:100%;height:44px;padding:0 14px;border:1px solid #e5e7eb;border-radius:8px;font-size:15px;margin-bottom:16px;outline:none}
.input-box:focus{border-color:#dc2626}
.btn{width:100%;height:46px;background:#dc2626;color:#fff;border:none;border-radius:8px;font-size:15px;font-weight:500;cursor:pointer}
.btn:hover{background:#b91c1c}
.card{
  margin-top:24px;
  padding:25px 20px;
  background:#ffffff;
  border:2px solid #dc2626;
  border-radius:16px;
  text-align:center;
  display:none;
  position:relative;
  overflow:hidden;
  width:100%;
  max-width:380px;
  aspect-ratio:1/1.2; /* 调整为更适合朋友圈的竖版比例 */
  margin-left:auto;
  margin-right:auto;
}
.card.show{display:block}
.logo{width:120px;margin:0 auto 15px}
.card-header{
    font-size:16px;
    font-weight:600;
    color:#dc2626;
    margin-bottom:10px;
    border-bottom:1px solid #f3f4f6;
    padding-bottom:10px;
}
.name{font-size:24px;font-weight:700;color:#111827;margin:15px 0;letter-spacing:1px}
.id-label{font-size:14px;color:#6b7280;margin-bottom:8px}
.id-code{font-size:20px;font-weight:700;color:#dc2626;letter-spacing:2px;margin-bottom:20px}
.seal{
  position:absolute;
  bottom:20px;
  right:20px;
  width:100px;
  opacity:0.7;
  transform:rotate(15deg);
}
.footer-note{
    font-size:11px;
    color:#9ca3af;
    position:absolute;
    bottom:10px;
    left:50%;
    transform:translateX(-50%);
    width:90%;
    line-height:1.4;
}
.save-btn{margin-top:20px;width:100%;height:44px;background:#16a34a;color:#fff;border:none;border-radius:8px;font-size:14px;display:none}
.save-btn:hover{background:#15803d}
/* 增加归属感的装饰元素 */
.card::before{
    content:"";
    position:absolute;
    top:10px;
    left:10px;
    right:10px;
    height:2px;
    background:linear-gradient(90deg, #dc2626, transparent, #dc2626);
}
.card::after{
    content:"";
    position:absolute;
    bottom:10px;
    left:10px;
    right:10px;
    height:2px;
    background:linear-gradient(90deg, #dc2626, transparent, #dc2626);
}
</style>
</head>
<body>
<div class="main">
    <div class="title">杨掌柜大学生专属名片</div>
    <div class="subtitle">输入抖音昵称/真实姓名，生成你的专属名片</div>
    <input class="input-box" id="userName" placeholder="请输入抖音昵称/真实姓名">
    <button class="btn" onclick="createCard()">生成名片</button>
    <div class="card" id="card">
        <div class="card-header">杨掌柜 · 大学生合伙人</div>
        <img class="logo" src="https://p.qqan.com/up/2025-12/173504724267444448.png" alt="杨掌柜Logo">
        <div class="name" id="showName"></div>
        <div class="id-label">专属身份编号</div>
        <div class="id-code" id="showId"></div>
        <img class="seal" src="https://p.qqan.com/up/2025-12/173504730167444448.png" alt="品牌印章">
        <div class="footer-note">该名片为品牌媒介发出，实际权限以媒介告知为准</div>
    </div>
    <button class="save-btn" id="saveBtn" onclick="saveImg()">保存名片图片</button>
</div>

<script src="https://html2canvas.hertzen.com/dist/html2canvas.min.js"></script>
<script>
function createCard(){
    let name = document.getElementById("userName").value.trim();
    if(!name){alert("请输入你的抖音昵称或真实姓名");return}
    let time = Date.now().toString().slice(-6);
    let rand = ("0000"+Math.floor(Math.random()*10000)).slice(-4);
    let id = "YZ-STU-" + time + "-" + rand; // 编号增加STU标识，更具专属感
    document.getElementById("showName").innerText = name;
    document.getElementById("showId").innerText = id;
    document.getElementById("card").classList.add("show");
    document.getElementById("saveBtn").style.display = "block";
}
function saveImg(){
    html2canvas(document.getElementById("card"),{useCORS:true}).then(canvas=>{
        let a = document.createElement("a");
        a.download = "杨掌柜大学生专属名片.png";
        a.href = canvas.toDataURL("image/png");
        a.click();
    });
}
</script>
</body>
</html>
