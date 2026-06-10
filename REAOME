

```html
<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=yes">
    <title>医疗器械工厂风险预测工具 | 의료기기 공장 위험 예측 도구</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }
        body {
            background: #eef2f5;
            font-family: 'Segoe UI', Roboto, 'Noto Sans KR', sans-serif;
            padding: 1.5rem;
            color: #1e2f3e;
        }
        .container {
            max-width: 1300px;
            margin: 0 auto;
        }
        h1 {
            text-align: center;
            font-size: 1.9rem;
            margin-bottom: 0.25rem;
            color: #0a4b6e;
        }
        .sub {
            text-align: center;
            margin-bottom: 2rem;
            color: #2c6e9e;
            font-weight: 500;
            display: flex;
            justify-content: center;
            gap: 1rem;
            flex-wrap: wrap;
        }
        .lang-switch {
            text-align: right;
            margin-bottom: 1rem;
        }
        .lang-btn {
            background: white;
            border: 1px solid #bdd4e0;
            padding: 0.3rem 1rem;
            border-radius: 30px;
            cursor: pointer;
            font-weight: bold;
            margin: 0 0.2rem;
            transition: 0.2s;
        }
        .lang-btn.active {
            background: #0a4b6e;
            color: white;
            border-color: #0a4b6e;
        }
        .card-grid {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(340px, 1fr));
            gap: 1.8rem;
            margin-top: 1rem;
        }
        .risk-card {
            background: white;
            border-radius: 28px;
            box-shadow: 0 10px 20px rgba(0,0,0,0.05);
            overflow: hidden;
            transition: transform 0.1s ease;
            border-top: 6px solid;
        }
        .card-header {
            padding: 1rem 1.5rem 0.5rem;
            background: #fafdff;
        }
        .card-header h2 {
            display: flex;
            align-items: center;
            gap: 10px;
            font-size: 1.6rem;
        }
        .card-header p {
            color: #4f6f8a;
            margin-top: 5px;
            font-size: 0.85rem;
        }
        .params {
            padding: 1rem 1.5rem;
            background: #f9fbfd;
            border-bottom: 1px solid #e2edf2;
        }
        .param-row {
            margin-bottom: 1.2rem;
        }
        .param-row label {
            display: block;
            font-weight: 600;
            margin-bottom: 6px;
            font-size: 0.85rem;
        }
        select, input[type="range"] {
            width: 100%;
            padding: 8px 10px;
            border-radius: 16px;
            border: 1px solid #cbdbe0;
            background: white;
            font-size: 0.9rem;
        }
        .range-value {
            display: inline-block;
            background: #e9f0f5;
            padding: 2px 8px;
            border-radius: 20px;
            font-size: 0.8rem;
            margin-left: 8px;
        }
        .predict-btn {
            background: #1f7a5a;
            color: white;
            border: none;
            width: 100%;
            padding: 12px;
            font-size: 1rem;
            font-weight: bold;
            border-radius: 40px;
            margin: 0.5rem 0 1rem 0;
            cursor: pointer;
            transition: 0.2s;
        }
        .predict-btn:hover {
            background: #0e5e44;
        }
        .result-area {
            padding: 1rem 1.5rem 1.5rem;
            border-top: 1px solid #e2edf2;
            background: white;
        }
        .risk-level {
            font-size: 1.2rem;
            font-weight: bold;
            padding: 10px;
            border-radius: 24px;
            text-align: center;
            margin-bottom: 12px;
        }
        .risk-high { background: #fce4e4; color: #b91c1c; }
        .risk-medium { background: #fff0db; color: #b45f06; }
        .risk-low { background: #e0f2e9; color: #156f39; }
        .advice {
            font-size: 0.9rem;
            background: #f0f6fa;
            padding: 10px 14px;
            border-radius: 20px;
            line-height: 1.4;
        }
        hr {
            margin: 15px 0;
        }
        .footer {
            text-align: center;
            margin-top: 2.5rem;
            font-size: 0.75rem;
            color: #6a8aaa;
        }
        @media (max-width: 700px) {
            body { padding: 0.8rem; }
        }
        .ko-text {
            font-weight: 400;
        }
    </style>
</head>
<body>
<div class="container">
    <div class="lang-switch">
        <button class="lang-btn active" data-lang="zh">中文</button>
        <button class="lang-btn" data-lang="ko">한국어</button>
    </div>
    <h1><span class="lang-zh">🏭 医疗器械产业安全风险预测工具</span><span class="lang-ko" style="display:none;">🏭 의료기기 산업 안전 위험 예측 도구</span></h1>
    <div class="sub">
        <span class="lang-zh">输入参数 → 实时评估风险等级 + 改善建议</span>
        <span class="lang-ko" style="display:none;">파라미터 입력 → 실시간 위험 평가 및 개선 권고</span>
    </div>

    <div class="card-grid">
        <!-- 辐射防护卡片 -->
        <div class="risk-card" style="border-top-color: #e7a614;">
            <div class="card-header">
                <h2>☢️ <span class="lang-zh">辐射防护</span><span class="lang-ko" style="display:none;">방사선 방호</span></h2>
                <p class="lang-zh">X射线/伽马射线设备 · 작업장 방사선 위험 평가</p>
                <p class="lang-ko" style="display:none;">X-선/감마선 장비 · 방사선 위험 평가</p>
            </div>
            <div class="params">
                <div class="param-row">
                    <label class="lang-zh">📊 辐射剂量率 (µSv/h)  <span id="doseVal" class="range-value">0.5</span></label>
                    <label class="lang-ko" style="display:none;">📊 선량률 (µSv/h) <span id="doseVal_ko" class="range-value">0.5</span></label>
                    <input type="range" id="doseRate" min="0" max="10" step="0.1" value="0.5">
                </div>
                <div class="param-row">
                    <label class="lang-zh">🛡️ 个人防护等级</label>
                    <label class="lang-ko" style="display:none;">🛡️ 개인 보호 수준</label>
                    <select id="radiationPPE">
                        <option value="3" class="lang-zh">完整 (铅衣+剂量计+警报器)</option>
                        <option value="2" class="lang-zh">基本 (仅铅衣+剂量计)</option>
                        <option value="1" class="lang-zh">不足 (无铅衣或剂量计缺失)</option>
                        <option value="3" class="lang-ko" style="display:none;">완벽 (납 보호복+선량계+경보기)</option>
                        <option value="2" class="lang-ko" style="display:none;">기본 (납 보호복+선량계만)</option>
                        <option value="1" class="lang-ko" style="display:none;">부족 (납 보호복 또는 선량계 없음)</option>
                    </select>
                </div>
                <div class="param-row">
                    <label class="lang-zh">🔧 联锁装置/屏蔽完整性</label>
                    <label class="lang-ko" style="display:none;">🔧 인터록 장치/차폐 무결성</label>
                    <select id="radiationShield">
                        <option value="3" class="lang-zh">良好 (定期检测, 功能正常)</option>
                        <option value="2" class="lang-zh">部分有效 (部分区域屏蔽老化)</option>
                        <option value="1" class="lang-zh">失效或缺失 (无联锁或屏蔽损坏)</option>
                        <option value="3" class="lang-ko" style="display:none;">우수 (정기 검사, 정상 작동)</option>
                        <option value="2" class="lang-ko" style="display:none;">부분 유효 (일부 차폐 노후화)</option>
                        <option value="1" class="lang-ko" style="display:none;">실패 또는 누락 (인터록 없음/차폐 손상)</option>
                    </select>
                </div>
            </div>
            <button class="predict-btn" data-scene="radiation"><span class="lang-zh">🔮 预测风险</span><span class="lang-ko" style="display:none;">🔮 위험 예측</span></button>
            <div class="result-area" id="resultRadiation">
                <div class="risk-level risk-low" id="radLevelText"><span class="lang-zh">⚡ 等待评估</span><span class="lang-ko" style="display:none;">⚡ 평가 대기 중</span></div>
                <div class="advice" id="radAdvice"><span class="lang-zh">点击上方按钮，输入参数后获得风险评级与建议</span><span class="lang-ko" style="display:none;">위 버튼을 눌러 매개변수를 입력하면 위험 등급과 권고사항을 받을 수 있습니다.</span></div>
            </div>
        </div>

        <!-- 生物安全卡片 -->
        <div class="risk-card" style="border-top-color: #2c8c5a;">
            <div class="card-header">
                <h2>🧫 <span class="lang-zh">生物安全</span><span class="lang-ko" style="display:none;">생물안전</span></h2>
                <p class="lang-zh">病原体/人体组织样本 · 병원체/인체조직 위험</p>
                <p class="lang-ko" style="display:none;">병원체/인체 조직 위험</p>
            </div>
            <div class="params">
                <div class="param-row">
                    <label class="lang-zh">🦠 生物危害等级 (BSL)</label>
                    <label class="lang-ko" style="display:none;">🦠 생물학적 위험 등급 (BSL)</label>
                    <select id="bioLevel">
                        <option value="1">BSL-1 (低风险微生物)</option>
                        <option value="2">BSL-2 (中等风险，如乙肝病毒)</option>
                        <option value="3">BSL-3 (高风险气溶胶传播)</option>
                    </select>
                </div>
                <div class="param-row">
                    <label class="lang-zh">🧤 生物安全柜使用 & PPE</label>
                    <label class="lang-ko" style="display:none;">🧤 생물안전작업대 사용 및 PPE</label>
                    <select id="bioPPE">
                        <option value="3">II级BSC + 全面防护 (N95+双层手套+护目镜)</option>
                        <option value="2">仅BSC或仅基本PPE (口罩+单层手套)</option>
                        <option value="1">无BSC或无适当PPE</option>
                    </select>
                </div>
                <div class="param-row">
                    <label class="lang-zh">🧪 废弃物处理规范</label>
                    <label class="lang-ko" style="display:none;">🧪 폐기물 처리 규정</label>
                    <select id="bioWaste">
                        <option value="3">立即高压灭菌+专用容器</option>
                        <option value="2">普通密封丢弃 (无灭菌)</option>
                        <option value="1">随意丢弃 / 无管理</option>
                    </select>
                </div>
            </div>
            <button class="predict-btn" data-scene="bio"><span class="lang-zh">🔮 预测风险</span><span class="lang-ko" style="display:none;">🔮 위험 예측</span></button>
            <div class="result-area" id="resultBio">
                <div class="risk-level risk-low"><span class="lang-zh">等待评估</span><span class="lang-ko" style="display:none;">평가 대기 중</span></div>
                <div class="advice"><span class="lang-zh">点击按钮，输入参数后获得生物安全风险评级</span><span class="lang-ko" style="display:none;">버튼을 클릭하여 생물안전 위험 평가를 받으세요.</span></div>
            </div>
        </div>

        <!-- 重物搬运卡片 -->
        <div class="risk-card" style="border-top-color: #3a7ca5;">
            <div class="card-header">
                <h2>🏋️ <span class="lang-zh">重物搬运</span><span class="lang-ko" style="display:none;">중량물 취급</span></h2>
                <p class="lang-zh">机械辅助 / 人工搬运 위험 평가</p>
                <p class="lang-ko" style="display:none;">기계 보조 / 수동 취급 위험 평가</p>
            </div>
            <div class="params">
                <div class="param-row">
                    <label class="lang-zh">📦 单次搬运重量 (kg)</label>
                    <label class="lang-ko" style="display:none;">📦 1회 취급 중량 (kg)</label>
                    <input type="range" id="weightKg" min="0" max="80" step="1" value="20">
                    <span id="weightVal" class="range-value">20 kg</span>
                </div>
                <div class="param-row">
                    <label class="lang-zh">🤝 辅助设备使用</label>
                    <label class="lang-ko" style="display:none;">🤝 보조 장비 사용</label>
                    <select id="liftingAid">
                        <option value="3">液压车/叉车/升降平台 (完全机械)</option>
                        <option value="2">手推车/半辅助 (部分人工)</option>
                        <option value="1">纯人力搬运 / 无辅助</option>
                    </select>
                </div>
                <div class="param-row">
                    <label class="lang-zh">🧍 人员培训与工效学</label>
                    <label class="lang-ko" style="display:none;">🧍 직원 교육 및 인간공학</label>
                    <select id="liftTraining">
                        <option value="3">定期培训 + 规范姿势 + 双人协作制度</option>
                        <option value="2">仅基本指导 / 偶尔提醒</option>
                        <option value="1">无培训或习惯不良</option>
                    </select>
                </div>
            </div>
            <button class="predict-btn" data-scene="lift"><span class="lang-zh">🔮 预测风险</span><span class="lang-ko" style="display:none;">🔮 위험 예측</span></button>
            <div class="result-area" id="ResultLift">
                <div class="risk-level risk-low"><span class="lang-zh">等待评估</span><span class="lang-ko" style="display:none;">평가 대기 중</span></div>
                <div class="advice"><span class="lang-zh">点击按钮评估重物搬运风险</span><span class="lang-ko" style="display:none;">버튼을 눌러 중량물 취급 위험을 평가하세요.</span></div>
            </div>
        </div>
    </div>
    <div class="footer">
        ⚠️ <span class="lang-zh">本预测基于规则模型，仅供参考，实际安全管理需结合现场评估。</span>
        <span class="lang-ko" style="display:none;">본 예측은 규칙 기반 모델로 참고용입니다. 실제 안전 관리는 현장 평가와 결합해야 합니다.</span>
    </div>
</div>

<script>
    // 语言切换逻辑
    const langButtons = document.querySelectorAll('.lang-btn');
    const zhElements = document.querySelectorAll('.lang-zh');
    const koElements = document.querySelectorAll('.lang-ko');

    function setLanguage(lang) {
        if (lang === 'zh') {
            zhElements.forEach(el => el.style.display = '');
            koElements.forEach(el => el.style.display = 'none');
            document.querySelectorAll('select option.lang-zh').forEach(opt => opt.style.display = '');
            document.querySelectorAll('select option.lang-ko').forEach(opt => opt.style.display = 'none');
            // 修正radio/select显示
            for(let sel of document.querySelectorAll('select')) {
                let val = sel.value;
                sel.innerHTML = Array.from(sel.options).map(opt => {
                    if(opt.classList.contains('lang-zh')) return `<option value="${opt.value}" ${opt.value==val ? 'selected' : ''}>${opt.innerText}</option>`;
                    return '';
                }).join('');
            }
        } else {
            zhElements.forEach(el => el.style.display = 'none');
            koElements.forEach(el => el.style.display = '');
            document.querySelectorAll('select option.lang-zh').forEach(opt => opt.style.display = 'none');
            document.querySelectorAll('select option.lang-ko').forEach(opt => opt.style.display = '');
            for(let sel of document.querySelectorAll('select')) {
                let val = sel.value;
                sel.innerHTML = Array.from(sel.options).map(opt => {
                    if(opt.classList.contains('lang-ko')) return `<option value="${opt.value}" ${opt.value==val ? 'selected' : ''}>${opt.innerText}</option>`;
                    return '';
                }).join('');
            }
        }
        langButtons.forEach(btn => {
            if(btn.getAttribute('data-lang') === lang) btn.classList.add('active');
            else btn.classList.remove('active');
        });
    }

    langButtons.forEach(btn => {
        btn.addEventListener('click', () => setLanguage(btn.getAttribute('data-lang')));
    });

    // 辅助显示实时数字
    const doseSlider = document.getElementById('doseRate');
    const doseValSpan = document.getElementById('doseVal');
    doseSlider.addEventListener('input', () => {
        doseValSpan.innerText = doseSlider.value;
        if(document.getElementById('doseVal_ko')) document.getElementById('doseVal_ko').innerText = doseSlider.value;
    });
    const weightSlider = document.getElementById('weightKg');
    const weightSpan = document.getElementById('weightVal');
    weightSlider.addEventListener('input', () => weightSpan.innerText = weightSlider.value + " kg");

    // 风险预测函数
    function predictRadiation() {
        let dose = parseFloat(doseSlider.value);
        let ppe = parseInt(document.getElementById('radiationPPE').value);
        let shield = parseInt(document.getElementById('radiationShield').value);
        // 风险分数 (0~100) 剂量越高越差，PPE shield 越低越差
        let doseScore = Math.min(100, (dose / 10) * 100); // 10µSv/h => 100分
        let ppeScore = (3 - ppe) * 33.33;
        let shieldScore = (3 - shield) * 33.33;
        let total = (doseScore * 0.5) + (ppeScore * 0.25) + (shieldScore * 0.25);
        let risk = total;
        let level = "";
        let adviceZh = "", adviceKo = "";
        if (risk >= 60) { level = "🔴 高风险"; adviceZh = "立即停用设备，检查屏蔽完整性，强制全员使用铅衣+警报器，并限制作业时间。"; adviceKo = "즉시 장비 사용 중지, 차폐 무결성 검사, 모든 작업자 납 보호복+경보기 착용 및 작업 시간 제한."; }
        else if (risk >= 30) { level = "🟡 中等风险"; adviceZh = "优化防护措施，增加个人剂量监测频率，考虑工程控制升级。"; adviceKo = "보호 조치 최적화, 개인 선량 모니터링 빈도 증가, 엔지니어링 제어 업그레이드 고려."; }
        else { level = "🟢 低风险"; adviceZh = "维持现有防护，定期检测设备联锁，继续培训。"; adviceKo = "현 보호 유지, 정기적 인터록 점검, 교육 지속."; }
        document.getElementById('radLevelText').innerHTML = `<span class="lang-zh">${level}</span><span class="lang-ko" style="display:none;">${level.replace('高风险','고위험').replace('中等风险','중간 위험').replace('低风险','낮은 위험')}</span>`;
        document.getElementById('radAdvice').innerHTML = `<span class="lang-zh">💡 ${adviceZh}</span><span class="lang-ko" style="display:none;">💡 ${adviceKo}</span>`;
        let riskDiv = document.getElementById('radLevelText');
        riskDiv.className = `risk-level ${risk>=60 ? 'risk-high' : (risk>=30 ? 'risk-medium' : 'risk-low')}`;
    }

    function predictBio() {
        let bioLvl = parseInt(document.getElementById('bioLevel').value);
        let ppe = parseInt(document.getElementById('bioPPE').value);
        let waste = parseInt(document.getElementById('bioWaste').value);
        let riskScore = 0;
        if(bioLvl === 3) riskScore += 50;
        else if(bioLvl === 2) riskScore += 30;
        else riskScore += 10;
        riskScore += (3-ppe)*20;
        riskScore += (3-waste)*20;
        let level = "", adviceZh="", adviceKo="";
        if (riskScore >= 70) { level = "🔴 高风险"; adviceZh = "立即停止操作，升级生物安全柜至II级，强制使用N95+护目镜，并完善灭菌流程。"; adviceKo = "작업 중단, BSC 업그레이드, N95+보안경 의무화, 멸균 절차 개선."; }
        else if (riskScore >= 40) { level = "🟡 中等风险"; adviceZh = "加强培训，确保每次操作均在BSC内完成，规范废弃物高压灭菌。"; adviceKo = "교육 강화, 모든 작업 BSC 내에서 수행, 폐기물 고압멸균 규정 준수."; }
        else { level = "🟢 低风险"; adviceZh = "继续保持标准PPE及BSC使用，定期审核生物安全规范。"; adviceKo = "표준 PPE 및 BSC 사용 유지, 정기적 생물안전 감사."; }
        let resultDiv = document.getElementById('resultBio');
        resultDiv.querySelector('.risk-level').innerHTML = `<span class="lang-zh">${level}</span><span class="lang-ko" style="display:none;">${level.replace('高风险','고위험').replace('中等风险','중간 위험').replace('低风险','낮은 위험')}</span>`;
        resultDiv.querySelector('.advice').innerHTML = `<span class="lang-zh">💡 ${adviceZh}</span><span class="lang-ko" style="display:none;">💡 ${adviceKo}</span>`;
        let rl = resultDiv.querySelector('.risk-level');
        rl.className = `risk-level ${riskScore>=70 ? 'risk-high' : (riskScore>=40 ? 'risk-medium' : 'risk-low')}`;
    }

    function predictLift() {
        let weight = parseFloat(weightSlider.value);
        let aid = parseInt(document.getElementById('liftingAid').value);
        let training = parseInt(document.getElementById('liftTraining').value);
        let weightScore = 0;
        if(weight > 50) weightScore = 70;
        else if(weight > 25) weightScore = 40;
        else weightScore = 15;
        let aidScore = (3-aid)*25;
        let trainingScore = (3-training)*20;
        let total = weightScore*0.5 + aidScore*0.3 + trainingScore*0.2;
        let level="", adviceZh="", adviceKo="";
        if(total >= 65) { level = "🔴 高风险"; adviceZh = "立即改用机械搬运，严格执行双人操作，每周进行工效学培训。"; adviceKo = "즉시 기계 취급으로 전환, 2인 작업 규칙 엄수, 매주 인간공학 교육."; }
        else if(total >= 35) { level = "🟡 中等风险"; adviceZh = "增加辅助设备，推广正确弯腰抬举姿势，设立重量限制标识。"; adviceKo = "보조 장비 추가, 올바른 들어올리기 자세 교육, 중량 제한 표지 부착."; }
        else { level = "🟢 低风险"; adviceZh = "维持现有良好操作，定期检查搬运工具。"; adviceKo = "현행 우수 작업 유지, 취급 도구 정기 점검."; }
        let resDiv = document.getElementById('ResultLift');
        resDiv.querySelector('.risk-level').innerHTML = `<span class="lang-zh">${level}</span><span class="lang-ko" style="display:none;">${level.replace('高风险','고위험').replace('中等风险','중간 위험').replace('低风险','낮은 위험')}</span>`;
        resDiv.querySelector('.advice').innerHTML = `<span class="lang-zh">💡 ${adviceZh}</span><span class="lang-ko" style="display:none;">💡 ${adviceKo}</span>`;
        let rl = resDiv.querySelector('.risk-level');
        rl.className = `risk-level ${total>=65 ? 'risk-high' : (total>=35 ? 'risk-medium' : 'risk-low')}`;
    }

    // 绑定按钮
    document.querySelector('[data-scene="radiation"]').addEventListener('click', predictRadiation);
    document.querySelector('[data-scene="bio"]').addEventListener('click', predictBio);
    document.querySelector('[data-scene="lift"]').addEventListener('click', predictLift);

    // 初始化事件显示联动
    setLanguage('zh');
    // 初始值展示
    predictRadiation();
    predictBio();
    predictLift();
</script>
</body>
</html>
```

