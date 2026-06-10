<!DOCTYPE html>
<html lang="zh-CN">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, viewport-fit=cover">
    <title>医疗器械产业安全指南 | 의료기기 산업 안전 가이드 - 中韩对照</title>
    <!-- Font Awesome 6 (免费图标库) -->
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0-beta3/css/all.min.css">
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body {
            background: #f4f7fc;
            font-family: 'Segoe UI', Roboto, 'Noto Sans KR', 'Malgun Gothic', system-ui, -apple-system, sans-serif;
            line-height: 1.5;
            color: #1a2c3e;
            padding: 2rem 1rem;
        }

        .container {
            max-width: 1400px;
            margin: 0 auto;
        }

        /* 头部区域 */
        .header {
            text-align: center;
            margin-bottom: 3rem;
        }

        .header h1 {
            font-size: 2.2rem;
            background: linear-gradient(135deg, #0b5e7e, #1b7e5c);
            background-clip: text;
            -webkit-background-clip: text;
            color: transparent;
            margin-bottom: 0.5rem;
            letter-spacing: -0.3px;
        }

        .header .sub {
            font-size: 1.1rem;
            color: #2c6e9e;
            font-weight: 500;
            display: flex;
            justify-content: center;
            gap: 1.5rem;
            flex-wrap: wrap;
            margin-top: 0.5rem;
        }

        .header .sub span {
            background: #eef2f5;
            padding: 0.2rem 1rem;
            border-radius: 30px;
            font-size: 0.9rem;
        }

        .badge {
            background: #d9eaf3;
            display: inline-block;
            padding: 0.2rem 0.9rem;
            border-radius: 20px;
            font-size: 0.8rem;
            margin-bottom: 1rem;
        }

        /* 场景卡片 */
        .scene-card {
            background: white;
            border-radius: 28px;
            box-shadow: 0 10px 25px -5px rgba(0, 0, 0, 0.05), 0 8px 10px -6px rgba(0, 0, 0, 0.02);
            margin-bottom: 3rem;
            overflow: hidden;
            transition: all 0.2s ease;
            border: 1px solid #e2edf2;
        }

        .scene-header {
            padding: 1.5rem 2rem 0.8rem 2rem;
            background: #ffffff;
            border-bottom: 3px solid;
            display: flex;
            align-items: center;
            gap: 12px;
            flex-wrap: wrap;
        }

        .scene-icon {
            font-size: 2.2rem;
            background: #eef3fa;
            width: 55px;
            height: 55px;
            display: inline-flex;
            align-items: center;
            justify-content: center;
            border-radius: 60px;
        }

        .scene-title {
            font-size: 1.8rem;
            font-weight: 700;
        }

        .scene-title small {
            font-size: 1rem;
            font-weight: 400;
            color: #4a627a;
            margin-left: 10px;
        }

        .scene-desc {
            padding: 1.2rem 2rem;
            background: #f9fdfe;
            border-bottom: 1px solid #e0edf2;
        }

        .risk-double {
            display: flex;
            flex-wrap: wrap;
            gap: 1.5rem;
        }

        .risk-box {
            flex: 1;
            min-width: 200px;
            background: white;
            padding: 0.8rem 1rem;
            border-radius: 20px;
            box-shadow: 0 1px 2px rgba(0,0,0,0.03);
            border-left: 5px solid #cbdde6;
        }

        .risk-box .lang-label {
            font-weight: 700;
            font-size: 0.75rem;
            text-transform: uppercase;
            letter-spacing: 1px;
            color: #3c7a9e;
            margin-bottom: 8px;
            display: flex;
            align-items: center;
            gap: 6px;
        }

        .risk-box p {
            font-size: 0.95rem;
            color: #1f3b4a;
        }

        /* 表格区域 (SOP) */
        .section-title {
            font-size: 1.4rem;
            font-weight: 600;
            margin: 1rem 0 1rem 0;
            padding: 0 2rem;
            display: flex;
            align-items: center;
            gap: 12px;
        }

        .table-wrapper {
            overflow-x: auto;
            margin: 0 2rem 1.5rem 2rem;
            border-radius: 20px;
            border: 1px solid #e2edf2;
            background: white;
        }

        .sop-table {
            width: 100%;
            border-collapse: collapse;
            font-size: 0.9rem;
            min-width: 500px;
        }

        .sop-table th {
            background: #eef3f9;
            padding: 12px 12px;
            text-align: left;
            font-weight: 600;
            color: #1f5e7a;
            border-bottom: 1px solid #cfdfe8;
        }

        .sop-table td {
            padding: 12px 12px;
            border-bottom: 1px solid #e9f0f3;
            vertical-align: top;
        }

        .sop-table tr:last-child td {
            border-bottom: none;
        }

        .step-num {
            font-weight: 700;
            color: #0f6b8c;
            width: 60px;
        }

        /* 应急措施 左右对照 */
        .emergency-section {
            padding: 0 2rem 2rem 2rem;
        }

        .emer-title {
            font-size: 1.2rem;
            font-weight: 700;
            margin: 1rem 0 0.8rem 0;
            color: #bc4e2c;
            display: flex;
            align-items: center;
            gap: 8px;
        }

        .emer-grid {
            display: grid;
            grid-template-columns: 1fr 1fr;
            gap: 1.8rem;
            background: #fefaf5;
            padding: 1.2rem 1.5rem;
            border-radius: 24px;
            border: 1px solid #f0e2d4;
        }

        .emer-col {
            background: white;
            border-radius: 20px;
            padding: 1rem 1.2rem;
            box-shadow: 0 1px 3px rgba(0,0,0,0.05);
        }

        .emer-col h4 {
            font-weight: 700;
            font-size: 1rem;
            margin-bottom: 12px;
            border-left: 4px solid #bc4e2c;
            padding-left: 10px;
        }

        .emer-col ul {
            padding-left: 1.2rem;
        }

        .emer-col li {
            margin-bottom: 8px;
            line-height: 1.4;
        }

        /* 脚注 */
        .footer {
            text-align: center;
            margin-top: 3rem;
            padding: 1.5rem;
            font-size: 0.8rem;
            color: #5e7e97;
            border-top: 1px solid #cfe1e9;
        }

        /* 响应式 */
        @media (max-width: 780px) {
            body {
                padding: 1rem 0.8rem;
            }
            .scene-header {
                padding: 1rem 1.2rem;
            }
            .scene-title {
                font-size: 1.4rem;
            }
            .scene-desc, .section-title, .table-wrapper, .emergency-section {
                padding-left: 1rem;
                padding-right: 1rem;
            }
            .table-wrapper {
                margin-left: 1rem;
                margin-right: 1rem;
            }
            .emer-grid {
                grid-template-columns: 1fr;
                gap: 1rem;
            }
            .risk-double {
                flex-direction: column;
            }
        }

        /* 辐射边框颜色 */
        .scene-card[data-scene="radiation"] .scene-header {
            border-bottom-color: #e7a614;
        }
        .scene-card[data-scene="bio"] .scene-header {
            border-bottom-color: #2c8c5a;
        }
        .scene-card[data-scene="lift"] .scene-header {
            border-bottom-color: #3a7ca5;
        }

        i.icon-margin {
            margin-right: 6px;
        }
        .kt-text {
            font-weight: 500;
            letter-spacing: 0.2px;
        }
    </style>
</head>
<body>
<div class="container">
    <div class="header">
        <div class="badge"><i class="fas fa-industry"></i> 医疗器械产业工厂 · 의료기기 산업 공장</div>
        <h1>⚕️ 产业安全风险场景指南 <span style="font-size: 1.8rem;">&</span> 📘 산업 안전 위험 시나리오</h1>
        <div class="sub">
            <span><i class="fas fa-language"></i> 中韩对照 · 중한 대조</span>
            <span><i class="fas fa-hard-hat"></i> SOP + 비상 조치</span>
        </div>
        <p style="margin-top: 1rem; max-width: 800px; margin-left: auto; margin-right: auto; color: #3f6b85;">辐射防护 · 生物安全 · 重物搬运 | 操作流程及应急措施即时对照，保障工厂一线作业安全</p>
    </div>

    <!-- 场景1: 辐射防护 -->
    <div class="scene-card" data-scene="radiation">
        <div class="scene-header">
            <div class="scene-icon"><i class="fas fa-radiation" style="color:#e7a614;"></i></div>
            <div class="scene-title">辐射防护 <small>방사선 방호</small></div>
        </div>
        <div class="scene-desc">
            <div class="risk-double">
                <div class="risk-box"><div class="lang-label"><i class="fas fa-flag-china"></i> 中文风险描述</div><p>在医疗器械工厂中，涉及X射线检测设备、医用直线加速器、伽马射线灭菌装置等，可能产生电离辐射。长期或高剂量暴露会导致组织损伤、癌症风险增加。必须严格遵循防护流程。</p></div>
                <div class="risk-box"><div class="lang-label"><i class="fas fa-flag-south-korea"></i> 한국어 위험 설명</div><p>의료기기 공장에서 X-ray 검사 장비, 의료용 선형가속기, 감마선 멸균 장치 등이 사용될 경우 전리 방사선이 발생할 수 있습니다. 장기간 또는 고용량 노출은 조직 손상 및 암 발생 위험을 높입니다. 방호 절차를 엄격히 따라야 합니다.</p></div>
            </div>
        </div>

        <div class="section-title"><i class="fas fa-clipboard-list"></i> 标准操作流程 (SOP) · 표준 작업 절차</div>
        <div class="table-wrapper">
            <table class="sop-table">
                <thead>
                    <tr><th>단계 / 步骤</th><th>중국어 작업 지침 (中文)</th><th>한국어 작업 지침 (韓文)</th></tr>
                </thead>
                <tbody>
                    <tr><td class="step-num">1</td><td>进入辐射控制区前，佩戴个人剂量计和辐射警报器。</td><td>방사선 관리 구역에 들어가기 전에 개인 선량계와 방사선 경보기를 착용하십시오.</td></tr>
                    <tr><td class="step-num">2</td><td>确认设备联锁装置、警示灯及屏蔽门正常工作。</td><td>장비 인터록 장치, 경고등 및 차폐문이 정상 작동하는지 확인하십시오.</td></tr>
                    <tr><td class="step-num">3</td><td>操作时站在铅屏蔽屏后，并使用远程操控工具。</td><td>작업 시 납 차폐 스크린 뒤에 서서 원격 조작 도구를 사용하십시오.</td></tr>
                    <tr><td class="step-num">4</td><td>每两小时记录一次累计剂量值，若接近限值立即停止工作。</td><td>2시간마다 누적 선량 값을 기록하고, 한도에 근접하면 즉시 작업을 중단하십시오.</td></tr>
                    <tr><td class="step-num">5</td><td>工作结束后按指定路线退出，脱下防护服并单独存放于铅柜。</td><td>작업 종료 후 지정된 경로로 퇴실하고 보호복을 벗어 납 캐비닛에 별도 보관하십시오.</td></tr>
                </tbody>
            </table>
        </div>

        <div class="emergency-section">
            <div class="emer-title"><i class="fas fa-truck-medical"></i> 应急措施 · 비상 조치</div>
            <div class="emer-grid">
                <div class="emer-col"><h4><i class="fas fa-exclamation-triangle"></i> 中文应急措施</h4><ul><li>立即按下紧急停止按钮，封锁辐射区域，禁止人员进入。</li><li>所有人员迅速沿撤离通道离开，到指定集合点清点人数。</li><li>立即报告安全负责人并启动应急预案，通知专业辐射应急小组。</li><li>受照人员不得自行离开，等候专业去污和紧急医学检查。</li></ul></div>
                <div class="emer-col"><h4><i class="fas fa-exclamation-triangle"></i> 한국어 비상 조치</h4><ul><li>즉시 비상 정지 버튼을 누르고 방사선 구역을 봉쇄하십시오.</li><li>모든 인원은 신속하게 대피 통로를 따라 지정 집결지로 이동하십시오.</li><li>안전 책임자에게 보고하고 비상 대응 계획을 가동하며 전문 방사선 대응팀에 연락하십시오.</li><li>피폭자는 스스로 이동하지 말고 전문 제독 및 응급 건강 검진을 기다리십시오.</li></ul></div>
            </div>
        </div>
    </div>

    <!-- 场景2: 生物安全 -->
    <div class="scene-card" data-scene="bio">
        <div class="scene-header">
            <div class="scene-icon"><i class="fas fa-biohazard" style="color:#2c8c5a;"></i></div>
            <div class="scene-title">生物安全 <small>생물학적 안전</small></div>
        </div>
        <div class="scene-desc">
            <div class="risk-double">
                <div class="risk-box"><div class="lang-label"><i class="fas fa-flag-china"></i> 中文风险描述</div><p>医疗器械工厂可能接触病原体、人体组织样本、生物指示剂及污染性医疗器械。暴露可导致感染、过敏或职业性传播疾病。必须加强二级生物安全防护。</p></div>
                <div class="risk-box"><div class="lang-label"><i class="fas fa-flag-south-korea"></i> 한국어 위험 설명</div><p>의료기기 공장에서는 병원체, 인체 조직 샘플, 생물학적 지시약 및 오염된 의료기기에 노출될 수 있습니다. 노출 시 감염, 알레르기 또는 직업성 전염병을 유발할 수 있으므로 2등급 생물안전 보호를 강화해야 합니다.</p></div>
            </div>
        </div>

        <div class="section-title"><i class="fas fa-clipboard-list"></i> 标准操作流程 (SOP) · 표준 작업 절차</div>
        <div class="table-wrapper">
            <table class="sop-table">
                <thead><tr><th>步骤 / 단계</th><th>中文操作</th><th>한국어 작업 지침</th></tr></thead>
                <tbody>
                    <tr><td class="step-num">1</td><td>进入生物安全区前，穿戴二级生物安全柜配套 PPE：隔离衣、双层手套、护目镜及N95口罩。</td><td>생물안전 구역에 들어가기 전에 2등급 생물안전작업대에 맞는 개인보호구(격리복, 이중 장갑, 보안경, N95 마스크)를 착용하십시오.</td></tr>
                    <tr><td class="step-num">2</td><td>所有操作必须在二级生物安全柜 (BSC) 内进行，禁止在开放台面处理生物危险物。</td><td>모든 작업은 반드시 2등급 생물안전작업대(BSC) 내에서 수행해야 하며, 개방형 작업대에서 생물학적 위험물을 취급하지 마십시오.</td></tr>
                    <tr><td class="step-num">3</td><td>工作结束后，使用有效消毒剂（0.5%次氯酸钠）擦拭台面及器械表面。</td><td>작업 종료 후 유효한 소독제(0.5% 차아염소산나트륨)로 작업대 및 기기 표면을 닦으십시오.</td></tr>
                    <tr><td class="step-num">4</td><td>所有污染性耗材及锐器放入专用生物危害垃圾袋/锐器盒，密封后高压灭菌。</td><td>모든 오염된 소모품 및 날카로운 도구는 전용 생물학적 위험 폐기물 봉투/날카로운 도구 용기에 넣고 밀봉한 후 고압멸균하십시오.</td></tr>
                    <tr><td class="step-num">5</td><td>完成操作后按顺序脱下防护用品，并进行手部消毒（七步洗手法）。</td><td>작업 완료 후 순서에 따라 보호구를 벗고 손 소독(7단계 세척법)을 시행하십시오.</td></tr>
                </tbody>
            </table>
        </div>

        <div class="emergency-section">
            <div class="emer-title"><i class="fas fa-truck-medical"></i> 应急措施 · 비상 조치</div>
            <div class="emer-grid">
                <div class="emer-col"><h4><i class="fas fa-ambulance"></i> 中文应急措施</h4><ul><li>皮肤意外接触血液/体液：立即用大量肥皂水冲洗至少15分钟。</li><li>粘膜或针刺伤暴露：挤压伤口并冲洗，立即报告安全主管，进行暴露后预防评估。</li><li>生物危险物质泄漏：疏散区域，封闭泄漏区，使用吸收材料覆盖，再消毒处理。</li><li>所有暴露事件需登记并追踪至少6个月健康状态。</li></ul></div>
                <div class="emer-col"><h4><i class="fas fa-ambulance"></i> 한국어 비상 조치</h4><ul><li>피부에 혈액/체액 우발적 접촉 시: 즉시 다량의 비눗물로 최소 15분간 세척하십시오.</li><li>점막 또는 바늘 상해 노출: 상처를 압박하고 흐르는 물에 씻은 후 안전 책임자에게 보고하여 노출 후 예방 평가를 받으십시오.</li><li>생물학적 위험물질 유출: 해당 구역을 대피시키고 봉쇄한 후 흡수 재료로 덮고 소독 처리를 수행하십시오.</li><li>모든 노출 사건은 등록하고 최소 6개월간 건강 상태를 추적 관찰하십시오.</li></ul></div>
            </div>
        </div>
    </div>

    <!-- 场景3: 重物搬运 -->
    <div class="scene-card" data-scene="lift">
        <div class="scene-header">
            <div class="scene-icon"><i class="fas fa-weight-hanging" style="color:#3a7ca5;"></i></div>
            <div class="scene-title">重物搬运 <small>중량물 취급</small></div>
        </div>
        <div class="scene-desc">
            <div class="risk-double">
                <div class="risk-box"><div class="lang-label"><i class="fas fa-flag-china"></i> 中文风险描述</div><p>医疗器械工厂需搬运大型影像设备、铅防护衣箱、高压灭菌罐等重物。不正确操作可能导致肌肉骨骼损伤、跌落砸伤或挤压事故。</p></div>
                <div class="risk-box"><div class="lang-label"><i class="fas fa-flag-south-korea"></i> 한국어 위험 설명</div><p>의료기기 공장에서는 대형 영상 장비, 납 보호복 상자, 고압 멸균 탱크 등 중량물을 취급해야 합니다. 부적절한 작업은 근골격계 손상, 낙하 충격 또는 압착 사고를 유발할 수 있습니다.</p></div>
            </div>
        </div>

        <div class="section-title"><i class="fas fa-clipboard-list"></i> 标准操作流程 (SOP) · 표준 작업 절차</div>
        <div class="table-wrapper">
            <table class="sop-table">
                <thead><tr><th>步骤 / 단계</th><th>中文操作</th><th>한국어 작업 지침</th></tr></thead>
                <tbody>
                    <tr><td class="step-num">1</td><td>搬运前评估物品重量，超出单人能力（>15kg）必须使用辅助设备或双人协作。</td><td>취급 전 물체 무게를 평가하고, 개인 능력 초과 시(>15kg) 반드시 보조 장비 또는 2인 협력을 사용하십시오.</td></tr>
                    <tr><td class="step-num">2</td><td>使用合适的工具：叉车、液压搬运车、升降平台或手推车，并检查设备完好性。</td><td>적절한 도구(지게차, 유압 카트, 리프트 플랫폼 또는 핸드 트럭)를 사용하고 장비의 완전성을 점검하십시오.</td></tr>
                    <tr><td class="step-num">3</td><td>搬运时保持背部挺直，屈膝下蹲，用腿部力量抬起，避免腰部扭转。</td><td>허리를 곧게 펴고 무릎을 구부려 쪼그린 자세에서 다리 힘으로 들어 올리며 허리 비틀기를 피하십시오.</td></tr>
                    <tr><td class="step-num">4</td><td>重物移动过程中确保通道畅通、无油污或障碍物，穿戴防砸鞋和安全手套。</td><td>중량물 이동 중 통로가 막히지 않고 기름때나 장애물이 없는지 확인하며, 안전화 및 안전 장갑을 착용하십시오.</td></tr>
                    <tr><td class="step-num">5</td><td>将负载稳定放置在指定区域，使用捆绑带或三角垫防止滚动/倾倒。</td><td>지정된 구역에 하중을 안정적으로 배치하고, 롤링/전도를 방지하기 위해 묶음 끈이나 삼각 받침을 사용하십시오.</td></tr>
                </tbody>
            </table>
        </div>

        <div class="emergency-section">
            <div class="emer-title"><i class="fas fa-truck-medical"></i> 应急措施 · 비상 조치</div>
            <div class="emer-grid">
                <div class="emer-col"><h4><i class="fas fa-hand-holding-heart"></i> 中文应急措施</h4><ul><li>重物砸伤/挤压肢体：立即停止作业，移开重物（如安全条件下），进行止血和包扎。</li><li>疑似骨折或脊椎损伤：不可随意移动伤者，固定伤处并立即呼叫急救。</li><li>扭伤或拉伤：遵循RICE原则（休息、冰敷、加压、抬高），并上报安全部门。</li><li>事故现场保留证据，分析原因，防止二次事故。</li></ul></div>
                <div class="emer-col"><h4><i class="fas fa-hand-holding-heart"></i> 한국어 비상 조치</h4><ul><li>중량물 낙하/사지 압착 시: 작업을 즉시 중단하고 안전한 경우 중량물을 제거한 후 지혈 및 붕대를 감습니다.</li><li>골절 또는 척추 손상 의심 시: 부상자를 함부로 움직이지 말고 부위를 고정한 후 즉시 응급처치를 요청하십시오.</li><li>염좌 또는 좌상: RICE 원칙(휴식, 얼음찜질, 압박, 거상)을 따르고 안전 부서에 보고하십시오.</li><li>사고 현장 증거를 보존하고 원인을 분석하여 2차 사고를 방지하십시오.</li></ul></div>
            </div>
        </div>
    </div>

    <!-- 额外附加 : 通用安全术语/警示 -->
    <div style="background: white; border-radius: 28px; padding: 1.5rem; margin-top: 1rem; border: 1px solid #e2edf2;">
        <div style="display: flex; align-items: center; gap: 12px; flex-wrap: wrap; justify-content: space-between;">
            <div><i class="fas fa-shield-alt" style="color:#1f7a5a;"></i> <strong>安全标识提示 · 안전 표지판</strong><br><span style="font-size:0.85rem;">⚠️ 辐射区域 ☣️ 生物危害 🏋️ 重物当心</span></div>
            <div><i class="fas fa-phone-alt"></i> <strong>紧急联络 · 비상 연락처</strong><br><span style="font-size:0.85rem;">工厂安全室 공장 안전실 | 应急救援 응급 구조</span></div>
            <div><i class="fas fa-clinic-medical"></i> <strong>定期培训 · 정기 교육</strong><br><span style="font-size:0.85rem;">每月安全演练 매월 안전 훈련</span></div>
        </div>
    </div>

    <div class="footer">
        <i class="far fa-copyright"></i> 医疗器械产业安全指南 – 中韩对照版 | 의료기기 산업 안전 가이드 - 중한 대조 버전<br>
        본 내용은 현장 안전 교육 참고용이며, 각 공장의 규정에 따라 적용하십시오. 本指南仅供参考，具体操作请遵循企业安全制度。
    </div>
</div>
</body>
</html>
