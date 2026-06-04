<!DOCTYPE html>
<html lang="zh-CN">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>AI辅助踝关节骨折远程康复平台</title>

<script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/jspdf/2.5.1/jspdf.umd.min.js"></script>

<style>

*{
margin:0;
padding:0;
box-sizing:border-box;
font-family:"Segoe UI",sans-serif;
}

body{
background:#f5f9fc;
color:#333;
}

header{
background:#2d89ef;
color:white;
padding:25px;
text-align:center;
}

header h1{
font-size:30px;
}

.container{
width:95%;
max-width:1200px;
margin:auto;
padding:20px;
}

.grid{
display:grid;
grid-template-columns:repeat(auto-fit,minmax(300px,1fr));
gap:20px;
}

.card{
background:white;
border-radius:15px;
padding:20px;
box-shadow:0 3px 10px rgba(0,0,0,0.08);
}

.card h2{
margin-bottom:15px;
color:#2d89ef;
}

input,select{
width:100%;
padding:10px;
margin-top:8px;
margin-bottom:12px;
border:1px solid #ccc;
border-radius:8px;
}

button{
background:#2d89ef;
color:white;
border:none;
padding:12px 20px;
border-radius:8px;
cursor:pointer;
margin-top:10px;
}

button:hover{
background:#1f6fd0;
}

.dashboard{
display:grid;
grid-template-columns:repeat(auto-fit,minmax(180px,1fr));
gap:15px;
margin-bottom:20px;
}

.metric{
background:white;
padding:20px;
border-radius:12px;
text-align:center;
box-shadow:0 2px 6px rgba(0,0,0,0.08);
}

.metric h3{
color:#2d89ef;
}

#advice{
font-size:18px;
font-weight:bold;
margin-top:10px;
}

footer{
text-align:center;
padding:20px;
margin-top:30px;
color:#666;
}

</style>
</head>

<body>

<header>
<h1>AI辅助踝关节骨折远程康复平台</h1>
<h3>AI 기반 발목 골절 원격 재활 플랫폼</h3>
</header>

<div class="container">

<div class="dashboard">

<div class="metric">
<h3>康复天数</h3>
<p id="days">30天</p>
<p>재활 일수</p>
</div>

<div class="metric">
<h3>疼痛评分</h3>
<p id="painDisplay">0</p>
<p>통증 점수</p>
</div>

<div class="metric">
<h3>ROM恢复率</h3>
<p id="romPercent">0%</p>
<p>ROM 회복률</p>
</div>

<div class="metric">
<h3>训练阶段</h3>
<p id="stageDisplay">1</p>
<p>훈련 단계</p>
</div>

</div>

<div class="grid">

<div class="card">

<h2>患者信息 / 환자 정보</h2>

<label>姓名 / 이름</label>
<input type="text" id="name" placeholder="请输入姓名">

<label>康复天数 / 재활 일수</label>
<input type="number" id="rehabDays" value="30">

</div>

<div class="card">

<h2>疼痛评估 / 통증 평가</h2>

<input
type="range"
min="0"
max="10"
value="0"
id="pain"
oninput="updatePain()">

<p id="painText">
疼痛评分：0 / 통증 점수：0
</p>

</div>

<div class="card">

<h2>ROM评估 / ROM 평가</h2>

<label>背屈角度(°) / 배굴</label>
<input type="number" id="dorsi" value="10">

<label>跖屈角度(°) / 저굴</label>
<input type="number" id="plantar" value="20">

<button onclick="calculateROM()">
计算恢复率
</button>

</div>

<div class="card">

<h2>训练阶段 / 훈련 단계</h2>

<select id="stage">

<option value="1">
第一阶段 / 1단계
</option>

<option value="2">
第二阶段 / 2단계
</option>

<option value="3">
第三阶段 / 3단계
</option>

</select>

<div id="trainingPlan">

踝泵运动、股四头肌训练<br>
발목 펌프 운동, 대퇴사두근 운동

</div>

</div>

<div class="card">

<h2>AI建议 / AI 권장사항</h2>

<button onclick="generateAdvice()">
生成建议
</button>

<div id="advice"></div>

</div>

<div class="card">

<h2>康复趋势图 / 재활 추세 그래프</h2>

<canvas id="trendChart"></canvas>

</div>

<div class="card">

<h2>PDF导出 / PDF 다운로드</h2>

<button onclick="downloadPDF()">
下载韩语PDF
</button>

</div>

</div>

</div>

<footer>
Digital Healthcare Platform © 2026
</footer>

<script>

let chart;

function updatePain(){

let value =
document.getElementById("pain").value;

document.getElementById("painText").innerHTML=
"疼痛评分："+value+
" / 통증 점수："+value;

document.getElementById("painDisplay").innerHTML=value;
}

function calculateROM(){

let dorsi=
parseInt(document.getElementById("dorsi").value);

let plantar=
parseInt(document.getElementById("plantar").value);

let percent=
Math.round(((dorsi+plantar)/70)*100);

if(percent>100) percent=100;

document.getElementById("romPercent").innerHTML=
percent+"%";
}

document.getElementById("stage")
.addEventListener("change",function(){

let stage=this.value;

document.getElementById("stageDisplay")
.innerHTML=stage;

let plan="";

if(stage==1){

plan=
"踝泵运动、股四头肌训练<br>발목 펌프 운동, 대퇴사두근 운동";

}

if(stage==2){

plan=
"平衡训练、弹力带训练<br>균형 운동, 탄성밴드 운동";

}

if(stage==3){

plan=
"步态训练、上下楼训练<br>보행 훈련, 계단 훈련";

}

document.getElementById("trainingPlan")
.innerHTML=plan;

});

function generateAdvice(){

let pain=
parseInt(document.getElementById("pain").value);

let rom=
document.getElementById("romPercent")
.innerText.replace("%","");

let advice="";

if(pain<=3 && rom>=70){

advice=
"恢复良好，可增加训练强度。<br><br>회복 상태가 양호하여 운동 강도를 증가할 수 있습니다.";

}

else if(pain<=6){

advice=
"建议维持当前训练计划。<br><br>현재 운동 계획을 유지하세요.";

}

else{

advice=
"建议减少训练并咨询医生。<br><br>운동 강도를 줄이고 의사 상담을 권장합니다.";

}

document.getElementById("advice")
.innerHTML=advice;
}

const ctx =
document.getElementById("trendChart");

chart = new Chart(ctx,{

type:"line",

data:{

labels:["1周","2周","3周","4周"],

datasets:[

{
label:"Pain",
data:[8,6,4,2]
},

{
label:"ROM",
data:[30,45,60,80]
}

]

}

});

async function downloadPDF(){

const { jsPDF } = window.jspdf;

const doc = new jsPDF();

let name=
document.getElementById("name").value || "Patient";

let pain=
document.getElementById("pain").value;

let rom=
document.getElementById("romPercent").innerText;

let stage=
document.getElementById("stage").value;

doc.setFontSize(18);
doc.text("Rehabilitation Report",20,20);

doc.setFontSize(12);

doc.text("Name : "+name,20,40);

doc.text("Pain Score : "+pain,20,55);

doc.text("ROM Recovery : "+rom,20,70);

doc.text("Training Stage : "+stage,20,85);

doc.text("Generated Date : "+new Date().toLocaleDateString(),20,100);

doc.save("rehabilitation_report.pdf");

}

updatePain();
calculateROM();

</script>

</body>
</html>
