# 智能穿戴设备替代物理车钥匙：面向新能源汽车主机厂的全面需求分析报告

**报告日期：2026年8月**　|　**分析对象：智能手表 / 智能手环 / 智能戒指 对 RKE / PKE / UWB 等物理钥匙功能的替代**　|　**适用读者：主机厂产品规划、智能网联、用户运营与生态合作团队**

---

## 1. 执行摘要

本报告围绕"智能穿戴设备（手表、手环、戒指）替代传统物理车钥匙"这一产品命题，按经典产品需求分析框架（市场洞察 → 用户分群 → 场景分析 → 功能定义 → 优先级 → 商业模式）展开，核心结论如下：

**第一，数字钥匙已从"配置亮点"进入"普及临界点"，可穿戴是下一个增量入口。** 2024年中国市场乘用车前装标配数字钥匙的新车交付量已超过1000万辆，同比增长54.52%，搭载率达47.51% [(搜狐)](https://www.sohu.com/a/875657635_115931) ；2025年1–4月渗透率进一步升至52.3%，其中蓝牙钥匙渗透率50.4%、NFC/RFID钥匙28.8%、UWB钥匙6.0% [(queniu.cn)](https://www.queniu.cn/post/27772.html) 。行业预测2027年装配率有望达80% [(腾讯新闻)](https://new.qq.com/rain/a/20250318A07BSP00) 。与此同时，2025年中国腕戴设备出货量达7390万台、同比增长20.8%，中国已是全球最大腕戴市场 [(IT之家)](https://www.ithome.com/0/927/606.htm) 。两条曲线的交汇点，就是"腕上钥匙"的需求窗口。

**第二，可穿戴车钥匙不是对物理钥匙的"完全替代"，而是"1个主力数字入口 + N层冗余"体系中的高粘性入口。** Gartner调查显示智能手表与手环的弃用率分别高达29%和30% [(lmtw.com)](https://lmtw.com/mzw/content/detail/id/182768) ，这意味着任何"唯一钥匙"策略都不可接受；正确的产品定位是：对存量可穿戴用户，手表钥匙是**零新增负担的最优钥匙形态**；对非可穿戴用户，物理钥匙/NFC卡片仍是必要冗余。

**第三，"BLE够用论"只在中低端车型的基础解闭锁场景成立。** BLE测距精度约±1米、响应延迟300–500ms，存在"飘忽感"且难以抵御中继攻击；UWB提供±10cm级测距、<100ms延迟和基于飞行时间的防中继能力，是"真无感进入"（靠近自动解锁、离开自动落锁、迎宾联动）的技术前提 [(CSDN博客)](https://blog.csdn.net/weixin_28716443/article/details/160542184) 。但UWB+BLE车端BOM成本约461元，是蓝牙方案（约123元）的3.7倍 [(微信公众平台)](http://mp.weixin.qq.com/s?__biz=MzI1MjkzMTcwOQ==&mid=2247642814&idx=5&sn=f3f63244262a1799a80b141eac2216b2) ，因此技术选型应按车型价格带分层：15万元以下 BLE+NFC，15–30万元 BLE+NFC 起步、UWB 高配，30万元以上 UWB 标配并复用雷达能力（脚踢、车内活体检测）摊薄成本。

**第四，手表对手机的依赖程度，决定了用户从"手机数字钥匙"迁移到"手表钥匙"的理由是否成立。** 近场解闭锁与启动（BLE/UWB/NFC 通道）在开通后由手表与车端直连完成、无需联网也无需手机在线；而远程控车需要蜂窝网络——若手表只能经蓝牙中继手机上网，则远程控车价值退化为"手机App的腕上快捷方式"，迁移理由薄弱。因此**手表钥匙的核心价值主张 = 近场无钥匙体系（替代物理钥匙）+ 脱离手机场景（替代手机钥匙）**，远程控车只是增值项而非迁移理由；产品设计上必须保证手表↔车近场直连独立可用，并优先支持 eSIM 独立通信机型。

**第五，商业模式建议"品牌生态合作为主、ODM/联名为辅、物理冗余兜底"。** 接入华为钱包、Apple CarKey、小米/OPPO/vivo 钱包等成熟生态，可以零硬件成本覆盖用户存量设备——华为穿戴数字车钥匙已支持问界、智界、比亚迪、深蓝、岚图、凯迪拉克、别克、阿维塔、领克、长城等约19个品牌 [(Huawei Consumer)](https://consumer.huawei.com/cn/support/content/zh-cn15892299/) ；而 ODM 自有品牌手表（如立欧实业为江淮、广汽传祺、长城、比亚迪供应车规级手表的模式 [(世展网)](https://www.shifair.com/wap/article_details/index/id/102642.html) ）在体验可控性、品牌运营和购车权益差异化上有独特价值，但需直面硬件成本、售后责任与约三成的弃用率风险。

---

## 2. 研究框架与分析方法

本报告采用经典产品需求分析框架，将命题拆解为八个相互衔接的分析模块：**产业背景与市场洞察（第3章）→ 用户分群分析（第4章）→ 使用场景分析（第5章）→ 设备形态对比（第6章）→ 技术功能重要性分析（第7章）→ 成本与体验增量分析（第8章）→ 合作模式分析（第9章）→ 手机依赖性与体验迁移分析（第10章）**，最终汇总为需求优先级与产品规划建议（第11章）和风险清单（第12章）。

分析方法上，报告综合使用：JTBD（Jobs-to-be-Done）场景拆解、KANO 功能分类模型、MoSCoW 优先级排序、BOM 成本对标、以及基于公开产业数据的二次分析。文中市场数据均来自 IDC、高工智能汽车研究院、佐思汽研、CAICV、中金公司、申万宏源、Gartner、J.D. Power 等公开研究或权威媒体报道；技术参数来自 CCC（Car Connectivity Consortium）数字钥匙规范及产业链公开资料；雷达图类定性评估为基于公开信息的产品分析判断，已在图注中明确标注。

需要说明的是，本命题天然处于"汽车电子"与"消费电子"两个产业的交叉地带：车端关注安全等级、成本与生命周期（10年以上），穿戴端关注用户粘性、生态与迭代速度（2–3年换机周期）。报告中多处结论的分歧点（如冗余策略、ODM 模式风险）都源于这一生命周期错配，这也是主机厂在立项时最容易低估的结构性问题。

---

## 3. 产业背景与市场洞察

### 3.1 数字钥匙：从配置亮点到普及临界点

汽车钥匙经历了机械钥匙、遥控钥匙（RKE）、无钥匙进入启动（PEPS/PKE）和数字钥匙四个阶段。数字钥匙的技术底座由 CCC 联盟 2021年7月发布的数字钥匙3.0规范确立：以 BLE 负责中远距离车辆发现与数据通道、UWB 负责厘米级安全测距、NFC 作为低电备份 [(jgvogel.cn)](https://file.jgvogel.cn/125/upload/resources/file/479607.pdf) 。2025年3月，CCC 进一步将 BLE 与 UWB 纳入认证体系，覆盖远程访问、无感进入、无感启动等关键功能，联盟成员已超200家，其中25%来自中国 [(iotexpo.com.cn)](https://m.iotexpo.com.cn/SH/NewsView/2C3A3D63BACAAF75.html) 。2025年7月发布的数字钥匙4.0进一步聚焦跨平台、跨版本的互操作与跨生态钥匙共享 [(VicOne)](https://vicone.com/zh/blog/from-fob-to-phone-how-ccc-digital-key-40-shapes-automotive-cybersecurity/) 。

![中国乘用车数字钥匙前装搭载率趋势](/assets/images/reports/wearable-digital-key/charts/c1_penetration.png)

渗透节奏上，数字钥匙的增长明显快于行业早期预期。佐思汽研数据显示，中国数字钥匙装配率近三年以年均超10个百分点的速度攀升，2024年整体装配率约40%，预计2025年达60%以上、2027年达80% [(腾讯新闻)](https://new.qq.com/rain/a/20250318A07BSP00) 。分技术路线看，蓝牙钥匙凭借成本与成熟度优势仍是绝对主力——2025年中国市场乘用车前装标配蓝牙钥匙新车上险量达1271.23万辆，渗透率55.31%，连续4年增长；UWB 则是增速最快的路线，2024年装配量同比增长354.6%，蔚来、极氪、鸿蒙智行、奔驰、宝马等 TOP5 品牌装配量占比合计77.1%，并从30万元以上车型向20万元以下快速渗透（如小鹏 P7+ 已标配 UWB 钥匙） [(phisemi.com)](https://www.phisemi.com/nd.jsp?id=81) 。此外，华为主导的星闪（NearLink）数字车钥匙已在问界 M9 上量产首发，成为 BLE/UWB 之外的第三势力 [(搜狐)](https://www.sohu.com/a/875657635_115931) 。

![数字钥匙分技术路线渗透率](/assets/images/reports/wearable-digital-key/charts/c2_tech_share.png)

### 3.2 可穿戴设备：足够大的用户基本盘与足够高的弃用率

可穿戴侧的基本盘同样可观。IDC 数据显示，2024年中国腕戴设备出货量达6116万台、同比增长19.3%，成为全球最大腕戴市场，占全球出货量的32.0%；其中智能手表4317万台（+18.8%）、手环1799万台（+20.2%） [(idc.com)](https://my.idc.com/getdoc.jsp?containerId=prCHC53244925) 。2025年进一步增至7390万台（+20.8%），智能手表5061万台、手环2329万台 [(IT之家)](https://www.ithome.com/0/927/606.htm) 。以一个年销百万辆级的新能源品牌为例，其目标客群（25–45岁、一二线城市、科技尝鲜者）与智能手表核心用户高度重合，**保守估计新能源车主中腕戴设备保有率已达40–60%**——这是"零硬件成本"获取钥匙入口的用户基础。

![中国腕戴设备市场出货量](/assets/images/reports/wearable-digital-key/charts/c4_wrist.png)

但必须直视另一面：**可穿戴是"高渗透、低粘性"并存的品类。** Gartner 对9500名消费者的调查显示，智能手表弃用率约29–30%、手环约30%，多数用户在数周新鲜感后仅保留健康追踪（使用率82%）和通知提醒（79%）等两三个核心功能 [(lmtw.com)](https://lmtw.com/mzw/content/detail/id/182768) 。智能戒指是增长最快的新形态——IDC 预计2025年全球出货约430万枚、同比增长49%，远超智能手表的6%——但绝对体量尚不足手表的3% [(36kr.com)](https://eu.36kr.com/zh/p/3629503396348935) 。这一结构直接决定了第四章的用户分群逻辑和第十二章的风险设计：**手表钥匙可以是"主力钥匙"，但永远不能是"唯一钥匙"。**

### 3.3 产业落地现状：三条路线均已跑通

当前市场上可穿戴车钥匙已形成三类可对照的落地范式。**其一是钱包生态接入范式**：华为钱包穿戴数字车钥匙已覆盖问界、智界、享界、尊界、深蓝、比亚迪、岚图、腾势、仰望、方程豹、凯迪拉克、别克、阿维塔、领克、猛士、长城等约19个品牌，支持 NFC 碰一碰、蓝牙无感解闭锁与启动、蓝牙遥控寻车；但手环系列仅支持 NFC 钥匙、不支持无感，且华为穿戴配对 iOS 手机时不支持车钥匙功能 [(Huawei Consumer)](https://consumer.huawei.com/cn/support/content/zh-cn15892299/) 。苹果 CarKey 已支持宝马、比亚迪、捷尼赛思、现代、起亚、奔驰等品牌，iOS 代码显示小米汽车、Lucid 及红旗、魏牌、奇瑞、岚图等中国品牌正在接入，iPhone 11 及以上与 Apple Watch Series 6 及以上可开通 UWB&NFC 钥匙，支持息屏解锁与低电关机刷卡 [(爱思助手)](https://m.i4.cn/article/51966.html) 。

**其二是"车企自生态"范式**：小米手表5与 SU7/YU7 深度联动，支持 NFC 车钥匙刷表解锁启动、表端远程控车（启停、解闭锁、闪灯鸣笛、前后备箱、空调通风）、车内融合设备中心腕上调节空调/座椅/音乐、导航关键节点振动提醒、小憩模式联动，甚至 SU7 Ultra 的 Boost 模式心率联动；599元的 REDMI Watch 6 也已支持小米汽车及宝马、比亚迪、仰望、腾势、方程豹、路特斯等品牌 NFC 车钥匙 [(IT之家)](https://www.ithome.com/0/908/350.htm) 。**其三是 ODM 定制范式**：深圳立欧实业（乐志云表）作为多家汽车集团的数字钥匙供应商，为江淮、广汽传祺、长城、比亚迪等提供车规级智能手表与数字车钥匙，主打"不改装、不加装、不动线"的整车厂配套模式 [(世展网)](https://www.shifair.com/wap/article_details/index/id/102642.html) ；OPPO Watch 2 也曾联合理想、比亚迪、长安欧尚等推出 NFC 车钥匙与远程车控 [(新京报)](https://m.bjnews.com.cn/detail/163533799714752.html) 。三条路线的成本结构、体验一致性与用户触达逻辑差异显著，构成第九章合作模式分析的现实基础。

---

## 4. 用户分群分析

### 4.1 分群框架：以"可穿戴使用现状"为第一分群轴

与常规 demographics 分群不同，本命题的第一分群轴应当是**用户当前的可穿戴设备使用状态**，因为它直接决定体验迁移成本的量级。我们将目标用户划分为五个群体：A 重度手表用户、B 轻度/场景型穿戴用户、C 智能戒指用户、D 弃用/闲置人群、E 不使用可穿戴的人群。这一分群轴再与"手机生态（iOS/华为/小米/其他安卓）"、"车型价格带"两个次级轴交叉，构成完整的需求地图。

五类群体的本质差异在于：**手表钥匙对 A 类用户是"已有设备的免费功能升级"，对 E 类用户则是"为一把钥匙买一块表并养成佩戴充电习惯"的重决策**。Gartner 数据显示约26%的智能手表和34%的手环是作为礼物购买的 [(lmtw.com)](https://lmtw.com/mzw/content/detail/id/182768) ，说明相当比例的设备并非用户主动选择，这部分人群的佩戴意愿天然脆弱；而 IDC 与行业观察显示健康监测是留存用户的核心留存理由（使用率82%） [(xiouwang.cn)](https://xiouwang.cn/oarticle/articles/7423.html) ，这提示主机厂：车钥匙功能在手表上的"对手"不是手机钥匙，而是手表本身能否留在用户手腕上。

### 4.2 五类群体画像与体验迁移成本

| 群体 | 规模与特征 | 当前钥匙行为 | 迁移到手表钥匙的成本 | 对主机厂的价值 |
|---|---|---|---|---|
| **A. 重度手表用户**（每天佩戴，含 eSIM 用户） | 腕戴用户中约40–50%；科技尝鲜、苹果/华为/小米生态深度用户 | 手机数字钥匙为主，物理钥匙备用 | **极低**：零新增设备、零新增习惯，仅需一次开通配对 | 最高——口碑传播者、功能深度使用者、车内联动功能的首批种子 |
| **B. 轻度/场景型穿戴用户**（运动时戴、间歇佩戴） | 腕戴用户中约20–30% | 物理钥匙+手机混用 | **低—中**：需建立"出门戴表"的场景触发，运动/游泳等场景迁移动力强 | 高——场景型价值（不带手机场景）的最直接受益者 |
| **C. 智能戒指用户** | 新兴小众（2025E全球约430万枚 [(36kr.com)](https://eu.36kr.com/zh/p/3629503396348935) ），但24小时佩戴粘性为所有形态中最高 | 手机钥匙为主 | **低**：佩戴习惯已养成，但戒指功能上限低（基本只有 NFC/BLE、无屏无交互） | 中——高端健康人群的"隐形钥匙"，适合作为备份入口而非主入口 |
| **D. 弃用/闲置人群**（买后落灰） | 约占手表/手环用户的29–30% [(lmtw.com)](https://lmtw.com/mzw/content/detail/id/182768)  | 物理钥匙为主 | **高**：手表钥匙可能成为其"重新戴表"的唤醒理由，也可能完全无感 | 中低——可被"钥匙刚需"唤醒的存量，但不可依赖 |
| **E. 不使用可穿戴的人群** | 车主中仍有40–60% | 物理钥匙为主，部分手机钥匙 | **最高**：购表成本（几百至数千元）+ 佩戴习惯养成 + 充电习惯养成三重负担 | 低——不应作为手表钥匙的目标用户，应以 NFC 卡片/手机钥匙服务 |

### 4.3 迁移成本的结构性拆解

体验迁移成本不仅是金钱成本，更是**习惯成本与心智成本**。对 A 类用户，迁移路径是"物理钥匙 → 手机钥匙 → 手表钥匙"的自然演进，每一步都减少了掏出设备、寻找设备的动作；而对 E 类用户，要求其为车钥匙功能改变数十年的携带习惯，迁移阻力远超功能收益，J.D. Power 调研也显示即便在数字化程度最高的美国市场，也只有39%的车主明确希望将智能手机作为数字钥匙使用 [(车家号)](https://chejiahao.m.autohome.com.cn/info/24497627) ——对可穿戴钥匙的主动需求比例只会更低。

因此对主机厂的关键启示是：**手表钥匙的正确打法不是"教育用户戴表"，而是"收割已经戴表的人"**。营销与产品资源应向 A/B 类用户倾斜（开通引导、默认推荐、仪式感设计），对 E 类用户则保留体面的物理/NFC 冗余方案，避免因"强推数字钥匙"损害品牌体验。同时，手表钥匙与车辆健康/充电/迎宾等场景的联动（如小米手表与车辆小憩模式、导航振动的联动 [(IT之家)](https://www.ithome.com/0/908/350.htm) ）反过来能成为手表的"留存理由"，对 D 类弃用人群形成唤醒——这是车-表双向赋能的独特价值，也是手表钥匙区别于手机钥匙的战略意义。

---

## 5. 使用场景分析

### 5.1 场景全景：以 JTBD 拆解"用车准入"任务

用户的根本任务（Job）不是"解锁车辆"，而是"**在任何状态下、以最小的动作成本和心理成本，安全地进入并使用车辆**"。围绕这一主任务，可拆解出进入、启动、离开、分享、远程管理、应急六个子任务。可穿戴设备在其中的价值分布极不均匀：在"进入"和"离开"两个高频子任务上价值最大，在"远程管理"上价值有限，在"应急"场景上则依赖冗余设计。

值得注意的是，"解锁"只是入口，数字钥匙更大的想象空间在于以数字 ID 打通"上车即登录"的个性化链路——UWB 识别到车主走近驾驶侧，即可联动座椅、后视镜、座舱账号、地图与音乐的自动就位，把"开车锁"和"车机交互"两个割裂场景用一个数字身份统一起来 [(电子工程专辑 EE Times China)](https://www.eet-china.com/mp/a361225.html) 。手表作为比手机更"贴身"的设备，在身份连续性上具有天然优势。

### 5.2 可穿戴优于手机的场景矩阵

| 场景 | 痛点（手机/物理钥匙） | 可穿戴的优势机制 | 体验增益评级 |
|---|---|---|---|
| **运动/跑步/游泳/健身后取车** | 不带手机或手机存包；物理钥匙无处安放 | eSIM 手表独立通信 [(Holafly eSIM)](https://esim.holafly.com/cn/blogs/apple-watch-esim-benefits/) ，手表是唯一随身设备；防水手表适配游泳场景 | ★★★★★ |
| **双手被占用**（抱娃、拎行李/快递、雨天打伞） | 掏手机/掏钥匙动作链条长 | 抬腕 NFC 碰刷或 UWB 无感进入，零掏取动作 | ★★★★★ |
| **近场无感进入与离开落锁** | 手机在口袋/包内信号受人体遮挡，BLE 测距"飘忽" [(搜狐)](https://www.sohu.com/a/875657635_115931)  | 手表佩戴于腕部、外露无遮挡，UWB 测距链路更稳定；靠近自动解锁、离开自动落锁 [(小鹏汽车)](https://www.xiaopeng.com/news/company_news/5532.html)  | ★★★★☆ |
| **手机没电/忘带手机** | 手机钥匙失效 | 手表 NFC 低电/熄屏可用；eSIM 手表独立在线；华为穿戴 NFC 钥匙无需联网 [(Huawei Consumer)](https://consumer.huawei.com/cn/support/content/zh-cn16029489/)  | ★★★★☆ |
| **车内轻交互** | 开车中掏手机分心 | 腕上调节空调/座椅/音乐；导航转向、红灯变绿振动提醒；小憩模式联动唤醒 [(IT之家)](https://www.ithome.com/0/908/350.htm)  | ★★★★☆ |
| **找车/轻量远程确认** | 打开App路径长 | 抬腕闪灯鸣笛、查看锁车状态与剩余电量 [(中关村在线智能穿戴频道)](https://smartwear.zol.com.cn/1106/11064148.html)  | ★★★☆☆ |
| **钥匙分享与临时授权**（代客泊车、家人用车、租车） | 物理钥匙需当面交接 | 手表/手机均可远程分享并设权限，手表侧适合"被授权人"轻量接收 | ★★★☆☆ |
| **仪式感与迎宾** | 物理钥匙无交互反馈 | 抬腕迎宾灯语、分段迎宾、表盘车控卡片 [(小鹏汽车)](https://www.xiaopeng.com/news/company_news/5532.html)  | ★★★☆☆ |

### 5.3 手机仍占优的场景

公平地说，手表并未全面胜出。**远程控车的主战场仍在手机**：远程开启空调预冷预热、充电管理、车辆定位与行车日志、钥匙权限的精细化管理（设置时效、限定功能、撤销）都依赖大屏交互与完整 App 功能，J.D. Power 调研显示远程锁定/解锁功能的使用率为34%、后备箱控制31%，这些功能的使用心智都锚定在手机上 [(车家号)](https://chejiahao.m.autohome.com.cn/info/24497627) 。此外，首次开通配对、固件升级、异常处理（解绑、挂失、换机迁移）也天然属于手机端流程。

由此得出场景策略：**手表承接"近场高频、轻操作、强时效"的动作，手机承接"远程低频、重管理、强信息"的动作，两者是分工而非替代**。主机厂在设计手表端功能时，应克制地把表端功能限定在"3秒内可完成的操作"（解锁/闭锁/闪灯/鸣笛/空调开关/尾门/查看状态），避免把 App 全家桶搬上1.5英寸屏幕——智能手表"功能冗余、用户低度使用"的教训（用户仅开发设备约20%的功能） [(中金在线财经号)](http://mp.cnfol.com/56373/article/1785208258-142594861.html) 不应在车上重演。

---

## 6. 不同可穿戴形态的对比分析

### 6.1 三形态能力画像

智能手表、手环、戒指在硬件能力上呈明显梯度。手表是唯一可承载完整钥匙体验的形态：可同时集成 NFC、BLE、UWB（Apple Watch Series 6 起内置 U1 芯片 [(icloudnews.net)](https://www.icloudnews.net/a/37710.html) 、华为 WATCH 4 Pro 支持 UWB 智慧控车 [(什么值得买)](https://post.smzdm.com/p/a95edp50) ）与 eSIM 独立通信，并有屏幕承载交互与反馈。手环受限于成本与体积，当前基本只支持 NFC 车钥匙、不支持蓝牙无感钥匙 [(Huawei Consumer)](https://consumer.huawei.com/cn/support/content/zh-cn15892299/) ，本质是"腕上 NFC 卡片"。戒指的佩戴粘性最高（24小时无感佩戴、续航5–9天），但无屏、无交互、天线空间极小，现阶段车钥匙能力以 NFC 为主（如 Ring One 支持特斯拉及 CCC DK 2.0 NFC 车辆解锁 [(bravechip.com)](http://www.bravechip.com/h-nd-20.html) 、凌拓 NexRing 支持无钥匙进入与启动 [(linktop.com.cn)](https://www.linktop.com.cn/yjzx/1-4082.html) ），UWB 受功耗与体积限制短期难以集成。

![不同可穿戴形态作为车钥匙的适配度](/assets/images/reports/wearable-digital-key/charts/c6_radar_form.png)

### 6.2 分形态的用户分群与场景优劣势

| 维度 | 智能手表 | 智能手环 | 智能戒指 |
|---|---|---|---|
| **目标用户** | A/B 类主力；苹果/华为/小米生态用户 | 价格敏感、轻度运动用户；下沉市场 | 高端健康人群、科技尝鲜者；24小时佩戴者 |
| **车钥匙功能上限** | NFC+BLE+UWB 全能力，无感进入+启动+遥控+车内交互 | 仅 NFC 碰刷解闭锁/启动 [(Huawei Consumer)](https://consumer.huawei.com/cn/support/content/zh-cn15892299/)  | NFC 碰刷为主，无感能力受限 |
| **优势场景** | 全场景：运动脱机、双手占用、车内轻交互、迎宾仪式感 | 运动场景、极致续航（2周+）、低门槛尝新 | 睡眠/全天候佩戴不断连，"永远在手上的备用钥匙" |
| **核心短板** | 续航1–21天需充电；弃用率约29–30% [(lmtw.com)](https://lmtw.com/mzw/content/detail/id/182768) ；价格500–25000元 | 无屏幕交互弱、无 UWB、无 eSIM，体验上限低 | 无屏无反馈、丢失率高（体积小）、生态最不成熟 |
| **市场规模** | 2025年中国出货5061万台 [(IT之家)](https://www.ithome.com/0/927/606.htm)  | 2025年中国出货2329万台 [(IT之家)](https://www.ithome.com/0/927/606.htm)  | 2025E全球约430万枚，+49% [(36kr.com)](https://eu.36kr.com/zh/p/3629503396348935)  |
| **主机厂策略** | **主战场**：全功能适配，优先 UWB/eSIM 机型 | **补充**：作为 NFC 钥匙的低成本载体，适合随车权益赠送 | **前瞻布局**：NFC 钥匙协议兼容即可，不投入专属开发 |

对主机厂而言，形态策略的结论是清晰的：**资源向手表集中（承担90%的体验创新），手环以 NFC 协议兼容"顺带支持"（边际成本近零，适合作为购车权益礼品），戒指保持协议层兼容、观察生态成熟度再决定是否加码**。戒指值得关注的理由不在当下体量，而在其"永不摘下的钥匙"属性恰好命中数字钥匙最痛的"忘带/没电"焦虑，一旦头部手机厂商（三星、荣耀、传闻中的苹果）将 UWB 或标准数字钥匙协议引入戒指品类，其作为"隐形备份钥匙"的价值会快速放大。

---

## 7. 技术功能重要性分析：UWB 到底值不值？

### 7.1 BLE / UWB / NFC / 星闪的能力对标

四条技术路线不是替代关系而是分工关系，CCC 3.0 的标准工作流清晰展示了这一点：80米范围内 BLE 扫描唤醒车辆并建立连接，10–20米 UWB 启动测距定位，3–10米触发迎宾区（车灯、喇叭），1–3米进入解锁区自动解锁并联动座椅/后视镜，上车后车内锚点确认钥匙在车内方可启动；NFC 则全程作为低电与应急备份 [(电子工程世界)](https://www.eeworld.com.cn/qcdz/eic693022.html) 。

| 指标 | BLE 5.1 | UWB (802.15.4z) | NFC (ISO 14443) | 星闪 NearLink |
|---|---|---|---|---|
| 定位精度 | ±1m | ±10cm | 接触式（<4cm） | 亚米级（目标厘米级） |
| 响应延迟 | 300–500ms | <100ms | 200–300ms | 低延迟（目标<100ms） |
| 典型工作距离 | 0–30m | 0–50m | 0–4cm | 0–30m+ |
| 防中继攻击 | 弱 | **强（ToF 安全测距）** | 强（物理近场） | 强（测距机制） |
| 功耗 | 中 | 较高（需 BLE 配合唤醒） | 极低（可无源） | 低 |
| 终端生态 | 所有手机/手表标配 | 中高端手机+少量手表（Apple Watch S6+、华为WATCH 4 Pro等） | 手机/手环/戒指普遍支持 | 华为生态内起步 |
| 车端BOM参考 | 约123元 | 与BLE组合约461元 | 约137元 | 商用初期，规模成本待验证 |

数据来源：CCC 规范解读与产业研究 [(CSDN博客)](https://blog.csdn.net/weixin_28716443/article/details/160542184) 

![数字钥匙技术路线能力画像](/assets/images/reports/wearable-digital-key/charts/c5_radar_tech.png)

### 7.2 "只有 BLE 就够用了吗？"——分车型价格带的回答

**对"能解锁、能启动"这一基础命题，BLE 确实够用**——这也是蓝牙钥匙渗透率50.4%而 UWB 仅6.0%的市场现实 [(queniu.cn)](https://www.queniu.cn/post/27772.html) 。但 BLE 的够用是有代价的：其一，**测距不稳导致"飘忽感"**——基于 RSSI 的蓝牙测距易受人体遮挡与多径干扰，靠近解锁的触发时机不稳定，行业对蓝牙钥匙"可用但称不上好用"的评价正源于此 [(搜狐)](https://www.sohu.com/a/875657635_115931) ；其二，**安全上限低**——BLE 无法从物理层抵御中继攻击，而中继攻击正是当前针对无钥匙系统最主流的盗车手段，UWB 的飞行时间测距使中继引入的额外延迟无处隐藏，是目前唯一从测距机制上根治该问题的方案 [(CSDN社区)](https://bbs.csdn.net/weixin_29901799/article/details/100158638) ；其三，**无感体验的完整性**——"靠近自动解锁、离开自动落锁、迎宾联动、按侧门精准识别"这一整套被高端用户视为"用了回不去"的体验，其技术前提就是厘米级定位 [(小鹏汽车)](https://www.xiaopeng.com/news/company_news/5532.html) 。

因此建议按车型价格带分层决策：**15万元以下车型，BLE+NFC 是最优性价比组合**，UWB 的超额成本（车端 BOM 约贵340元 [(微信公众平台)](http://mp.weixin.qq.com/s?__biz=MzI1MjkzMTcwOQ==&mid=2247642814&idx=5&sn=f3f63244262a1799a80b141eac2216b2) ）难以被目标用户感知与付费；**15–30万元车型，BLE+NFC 标配、UWB 作为高配或OTA升级选项**，与小鹏 P7+ 在18.68万元车型标配 UWB 所代表的下探趋势 [(电子工程专辑 EE Times China)](https://www.eet-china.com/mp/a361225.html) 保持同步；**30万元以上车型，UWB 应标配并通过"一套硬件多个功能"摊薄成本**——复用 UWB 锚点实现脚踢雷达尾门、车内活体检测（CPD）与 AVP 泊车定位，三个功能共享硬件后整体 BOM 已从约100美元降至70美元量级 [(微信公众平台)](http://mp.weixin.qq.com/s?__biz=MzI1MjkzMTcwOQ==&mid=2247642814&idx=5&sn=f3f63244262a1799a80b141eac2216b2) 。对可穿戴侧同理：手表 UWB（Apple Watch S6+、华为 WATCH 4 Pro 等）目前保有量有限，主机厂的 UWB 车端投资应主要按"手机 UWB"核算，手表 UWB 视为顺势增益。

### 7.3 KANO 功能重要性分层

将可穿戴车钥匙的候选功能放入 KANO 模型，可为研发投入排序提供直接依据。**必备型需求（缺了就是事故）**：解闭锁/启动成功率与稳定性、防中继与密钥安全（SE 安全芯片存储、测距密钥12小时有效期 [(carconnectivity.org)](https://carconnectivity.org/wp-content/uploads/2022/12/CCC_Digital_Key_Whitepaper_Approved-3.0_v2-1.pdf) ）、低电/熄屏可用（NFC 备份）、丢失后的远程注销与撤销 [(linktop.com.cn)](https://www.linktop.com.cn/yjzx/1-4082.html) 。**期望型需求（做得越好越满意）**：无感进入与离开落锁的触发稳定性、开通流程的简洁度（配对步骤从7步简化到3步以内是 CCC 3.0 的实测改进 [(CSDN博客)](https://blog.csdn.net/weixin_30568591/article/details/96857092) ）、钥匙分享的权限粒度（仅解锁/仅后备箱/限时/限次 [(nextgen-technology.com)](https://resources.nextgen-technology.com/zh/ccc-digital-key-3-latest) ）、多设备多钥匙管理。**兴奋型需求（超预期的传播点）**：迎宾灯语与仪式感、车内腕上交互（空调/座椅/音乐）、导航振动与小憩联动、心率等健康数据与驾驶模式联动（SU7 Ultra Boost 模式 [(搜狐)](https://www.sohu.com/a/969792239_362225) ）、手表没电关机后 NFC 刷卡。

需要警惕的是**兴奋型功能的边际衰减**：参考智能手表行业"功能冗余、用户仅使用约20%功能"的教训 [(中金在线财经号)](http://mp.cnfol.com/56373/article/1785208258-142594861.html) ，表端车控功能不宜贪多，每一处联动都应回答"为什么这个动作在手腕上做比在中控/手机上做更好"。

---

## 8. 替代物理钥匙：成本与体验增量分析

### 8.1 成本账：车端、云端与用户侧三笔账

**车端账**：传统 PEPS 系统车端 BOM 约150元、实体智能钥匙约100元，合计约250元/车；蓝牙钥匙方案约123元、NFC 钥匙约137元、NFC+BLE 约174元、UWB+BLE 约461元 [(电子工程世界论坛)](https://bbs.eeworld.com.cn/thread-1295548-1-1.html) 。这意味着一个反直觉的结论：**用 BLE/NFC 数字钥匙替代物理钥匙，车端成本不但不升反降**——省去实体钥匙的约100元/把（随车通常交付2把），即便计入数字钥匙模块，净成本仍可下降；真正增加成本的是 UWB（贵出的约340元购买的是无感体验与安全上限）。中金测算显示车端 UWB 数字钥匙系统单车价值量约1000元，其中 UWB 芯片占系统成本36.4%，国产芯片（纽瑞芯、驰芯等）量产正在快速拉低这一成本 [(财联社)](https://www.cls.cn/detail/1090122) 。

![车端钥匙系统BOM成本对比](/assets/images/reports/wearable-digital-key/charts/c3_bom.png)

**云端账**：数字钥匙需要云平台支撑钥匙签发、分享、撤销与生命周期管理，行业报价为开发费约200–300万元、License 维护费约30–50元/车 [(电子工程世界论坛)](https://bbs.eeworld.com.cn/thread-1295548-1-1.html) ；出海场景还需满足 R155/R156 等合规要求，银基科技联合腾讯云等推出的"全球数字钥匙云"类方案提供标准化接入与全托管运维，可降低主机厂多头对接成本 [(腾讯云)](https://cloud.tencent.com/developer/article/2678004) 。**用户侧账**：实体钥匙丢失补办通常需500–2000元且需到店，数字钥匙挂失与重新签发边际成本近零、全程线上完成；同时主机厂可彻底摆脱实体钥匙的库存、物流与售后补配体系。对可穿戴部分，**当用户使用存量手表时，主机厂为这一钥匙入口支付的硬件成本为零**——这是可穿戴钥匙相对"随车赠送 NFC 卡片/实体钥匙"最独特的成本结构优势。

### 8.2 体验增量：从"工具替代"到"入口重构"

体验增量可分为四层。**效率层**：消除掏钥匙/掏手机动作，无感进入把"上车前操作"压缩到零；**安全层**：UWB 防中继 + SE 芯片级密钥存储，安全上限高于可被中继攻击的传统 PKE [(CSDN社区)](https://bbs.csdn.net/weixin_29901799/article/details/100158638) ；**关系层**：钥匙的数字化使"分享"从线下交接变为远程秒级授权，并可设置时效与权限（如仅允许访问车辆但不允许驾驶），这是物理钥匙在原理上无法提供的能力 [(nextgen-technology.com)](https://resources.nextgen-technology.com/zh/ccc-digital-key-3-latest) ；**生态层**：手表钥匙是"人-车-家"互联的身份锚点，上车自动登录座舱账号、导航振动接力、健康数据联动驾驶模式，使钥匙从"开门工具"重构为"个性化用车入口" [(电子工程专辑 EE Times China)](https://www.eet-china.com/mp/a361225.html) 。

综合成本与体验可以给出替代策略的经济学结论：**BLE+NFC 替代物理钥匙是"降本+体验升级"的双赢，应尽快全系标配；UWB 是"付费买体验与安全上限"的选项，按价格带分层配置；可穿戴钥匙是在已建成的数字钥匙体系上"零硬件成本"新增的入口，边际投入主要是软件适配与生态对接费用，ROI 由存量可穿戴用户的体验升级与口碑贡献兑现。**

---

## 9. 合作模式分析：品牌商合作 vs ODM 合作

### 9.1 两条路线的优劣势全景

| 维度 | 品牌商生态合作（华为钱包/Apple CarKey/小米、OPPO、vivo 钱包等） | ODM/自有品牌定制手表（立欧实业模式 [(世展网)](https://www.shifair.com/wap/article_details/index/id/102642.html) ） |
|---|---|---|
| **用户覆盖** | 直接覆盖用户存量设备，A/B 类用户零门槛 | 仅覆盖随车触达用户，需用户换戴新表 |
| **硬件成本** | 主机厂零硬件投入 | 每台手表数百元 BOM，随车赠送则计入单车成本 |
| **上线速度** | 对接钱包协议即可，周期以月计 | 硬件定义-打样-车规验证-量产，周期以年计 |
| **体验一致性** | 受设备商策略制约（如华为手环仅 NFC、配对 iOS 不支持车钥匙 [(Huawei Consumer)](https://consumer.huawei.com/cn/support/content/zh-cn15892299/) ） | 完全自主定义，功能与交互可控 |
| **安全与认证** | 复用设备商 SE/钱包安全体系与 CCC 认证 | 需自建或采购安全方案并独立完成车规认证 |
| **数据与用户触点** | 触点与部分数据留在设备商生态 | 数据自有，手表成为车企私域运营入口 |
| **持续迭代** | 由设备商 OTA，车企搭便车 | 需自建穿戴软件团队，迭代能力弱于消费电子大厂 |
| **营销价值** | 借助品牌生态背书，但差异化弱 | 购车权益/联名礼盒的强差异化（"买车送表"） |
| **核心风险** | 生态碎片化需多头适配；设备商商务条款与排他；iOS/安卓割裂 | 弃用率29–30%导致权益沉没 [(lmtw.com)](https://lmtw.com/mzw/content/detail/id/182768) ；售后/换机责任；与用户已有手表冲突（无人愿戴两块表） |

### 9.2 决策建议：主辅结构与混合策略

**品牌生态合作应当是绝对主线。** 理由有三：其一，车钥匙是低频但高可靠要求的功能，用户不会为钥匙功能更换手表品牌，"适配用户的表"永远优于"给用户发表"；其二，头部生态的支持列表已在快速变长——Apple CarKey 正在接入小米、红旗、魏牌、奇瑞、岚图等中国品牌 [(ZAKER)](https://app.myzaker.com/news/article.php?pk=6a50534f8e9f0946eb468831) ，华为穿戴钥匙已覆盖19个品牌 [(Huawei Consumer)](https://consumer.huawei.com/cn/support/content/zh-cn15892299/) ，小米599元价位手表已支持宝马、比亚迪、路特斯等多品牌钥匙 [(sina.cn)](https://cj.sina.cn/articles/view/7857201856/1d45362c001903oth0?froms=ggmp) ——不接入生态等于主动放弃这些现成的触点；其三，生态合作的安全体系（SE 芯片、CCC 认证、钱包级风控）是车企自建难以低成本复现的。

**ODM/联名模式的合理定位是"营销与运营层"而非"钥匙底座"**：适用于三类情况——购车限时权益与礼盒（把手表作为高感知价值赠品，参考立欧为多家车企配套的模式 [(世展网)](https://www.shifair.com/wap/article_details/index/id/102642.html) ）；品牌粉丝运营与周边商城（类似车企精品的延伸）；对低价位车型目标用户（无穿戴设备人群）的"第一块表"渗透。但需严守两条纪律：ODM 手表的钥匙协议必须与车端主流数字钥匙体系同源（避免维护两套钥匙体系），且必须保留 NFC 卡片/物理钥匙冗余——一旦手表被弃用，用户用车准入不受影响。**对绝大多数主机厂，推荐"生态合作（覆盖存量）+ NFC 卡片（低成本冗余）+ 视品牌调性选择性开展联名手表（营销增量）"的三层结构**，不建议任何主机厂把自研/ODM 手表作为数字钥匙的主路径。

---

## 10. 可穿戴与手机的依赖性分析：双重体验迁移的核心命题

### 10.1 依赖性的技术解剖：哪些功能必须过手机？

这是全篇最能决定产品成败的问题。按通信路径拆解，手表车钥匙的功能可分为三类。**第一类：手表↔车近场直连，完全不依赖手机**——NFC 碰刷、BLE 无感解闭锁与启动、UWB 测距进入，密钥存储于手表 SE 芯片内，认证在手表与车端之间完成；华为官方文档明确"激活完成后，使用无感车钥匙时无需处于联网环境" [(Huawei Consumer)](https://consumer.huawei.com/cn/support/content/zh-cn16029489/) ，CCC 架构亦要求全部核心功能可离线完成 [(DevPress官方社区)](https://devpress.csdn.net/v1/article/detail/133095241) 。**第二类：依赖手机但仅为一次性流程**——开通、配对、分享、删除、挂失等管理操作，需要手机 App 与云端交互。**第三类：远程控车，必须依赖蜂窝网络**——此时手表有两条上网路径：经蓝牙中继手机（手机必须在附近且在线），或 eSIM/Wi-Fi 独立联网 [(Holafly eSIM)](https://esim.holafly.com/cn/blogs/apple-watch-esim-benefits/) 。

于是用户质疑"如果控车都要手表连手机，为什么多戴一块表"的答案是分层的：**对第一、二类功能，该质疑不成立**——近场钥匙恰恰是不依赖手机的部分，而且是手表体验最好的部分；**对第三类功能，质疑在"蓝牙中继"架构下成立**——若手表远程控车必须经手机中继，则其本质是把手机 App 的快捷方式放到手腕上，价值增量仅为"少掏一次手机"，在多数场景下不足以构成迁移理由。

### 10.2 双重迁移的动力学：用户为什么迁、凭什么留下

**第一重迁移（物理钥匙 → 手表钥匙）的动力**是完整的：无感进入免去掏取动作、不怕丢不怕忘（戴在手上）、可远程分享与撤销、丢失后可秒级注销（对比实体钥匙补配的500–2000元与到店流程）。**第二重迁移（手机钥匙 → 手表钥匙）的动力则是有条件的**，成立的条件是手表提供了手机无法覆盖的场景增量：运动/游泳等不带手机的场景（eSIM 独立通信是硬前提 [(Holafly eSIM)](https://esim.holafly.com/cn/blogs/apple-watch-esim-benefits/) ）、双手占用时的抬腕操作、手机没电时的兜底（手表 NFC 熄屏可用、低电关机刷卡 [(小鹏汽车)](https://www.xiaopeng.com/news/company_news/5532.html) ）、腕部外露带来的更稳定无感测距、以及车内轻交互（导航振动、小憩唤醒 [(IT之家)](https://www.ithome.com/0/908/350.htm) ）。

若一款手表钥匙方案把手机场景简单平移到表上（所有操作都需蓝牙连手机、表端只是 App 镜像），第二重迁移的动力就崩塌了——这正是大量"手表控车"功能上线后活跃度惨淡的原因。**产品纪律由此而来：① 近场钥匙能力必须与手机解耦，手表 SE 独立持钥、手表↔车直连认证；② 优先适配 eSIM 机型，让"不带手机也能控车、也能被找到"成为可宣传的核心场景；③ 表端远程功能只做"轻、急、短"操作（闪灯、鸣笛、空调、锁车确认），重管理留在手机；④ 用"手表专属场景"做营销话术（运动回家、抱娃上车、手机没电），而不是泛泛的"腕上控车"。** 同时必须正视生态现实：当前华为穿戴配对 iOS 手机不支持车钥匙、手环仅支持 NFC [(Huawei Consumer)](https://consumer.huawei.com/cn/support/content/zh-cn15892299/) ，安卓阵营 UWB 钥匙适配碎片化 [(新浪)](https://k.sina.com.cn/article_7879995959_1d5af323706801trjg.html) ，主机厂需按"手机生态 × 手表品牌"做兼容性矩阵公示，避免用户开通失败带来的负面口碑。

---

## 11. 需求优先级与产品规划建议

### 11.1 MoSCoW 优先级定义

综合前述分析，给出可直接进入产品立项的需求清单：

| 优先级 | 需求项 | 依据 |
|---|---|---|
| **P0 Must** | 手表 BLE+NFC 直连解锁/闭锁/启动（SE 独立持钥、离线可用）；手机端开通/分享/撤销全流程；低电 NFC 备份；丢失远程注销；主流钱包生态适配（华为、苹果、小米、OPPO、vivo、荣耀至少前三家） | 必备型需求与安全底线；生态覆盖决定可及用户规模 [(Huawei Consumer)](https://consumer.huawei.com/cn/support/content/zh-cn15892299/)  |
| **P1 Should** | UWB 无感进入（中高端车型标配、手表 UWB 机型适配）；eSIM 手表轻量远程控车（闪灯/鸣笛/空调/车况查看）；钥匙权限粒度（限时/限次/仅解锁）；兼容性矩阵公示与开通引导 | 期望型体验与差异化；UWB 按价格带分层 [(微信公众平台)](http://mp.weixin.qq.com/s?__biz=MzI1MjkzMTcwOQ==&mid=2247642814&idx=5&sn=f3f63244262a1799a80b141eac2216b2)  |
| **P2 Could** | 车内腕上交互（空调/座椅/音乐）；导航振动接力与小憩联动；迎宾灯语；智能戒指 NFC 钥匙协议兼容；手环 NFC 钥匙"顺带支持" | 兴奋型传播点；戒指/手环边际成本低 [(IT之家)](https://www.ithome.com/0/908/350.htm)  |
| **P3 Won't（本期不做）** | 自研/ODM 手表作为钥匙主路径；表端复杂车控全家桶；依赖手机蓝牙中继的表端远程控车（作为卖点宣传）；星闪钥匙规模投入（保持预研） | 弃用率与迁移逻辑不成立 [(lmtw.com)](https://lmtw.com/mzw/content/detail/id/182768) ；星闪生态待成熟 [(搜狐)](https://www.sohu.com/a/875657635_115931)  |

### 11.2 路线图与组织建议

落地节奏建议分三阶段。**第一阶段（0–6个月）：打底**——车端完成 BLE+NFC 数字钥匙全系标配（若尚未完成），接入2–3家头部钱包生态，跑通手表开通-使用-撤销全链路，建立兼容性测试矩阵与灰度机制。**第二阶段（6–18个月）：上探**——中高端车型搭载 UWB 并打通手表 UWB（Apple Watch、华为 WATCH UWB 机型），上线 eSIM 场景包（运动回家、离车落锁确认），启动车内腕上交互与小憩/导航联动等兴奋型功能。**第三阶段（18个月+）：扩生态**——戒指协议兼容、星闪跟进评估、UWB 雷达复用（CPD/脚踢）上车、出海市场数字钥匙合规（R155/R156）与区域生态适配 [(腾讯云)](https://cloud.tencent.com/developer/article/2678004) 。

组织层面有两点提醒。其一，**钥匙安全是"汽车级"命题而非"App 级"命题**：需建立覆盖 SE 密钥管理、中继攻击仿真、表端固件供应链安全的安全体系，并明确数字钥匙被盗用导致事故时主机厂、设备商、方案商之间的责任界定与保险安排——这是当前行业的法规空白点 [(CSDN社区)](https://bbs.csdn.net/weixin_29901799/article/details/100158638) 。其二，**把"开通率与活跃率"而非"支持机型数"作为北极星指标**：建议追踪手表钥匙开通率（目标：A/B 类用户中≥40%）、周活跃解锁占比（手表解锁次数/全部解锁次数）、无感进入触发成功率（目标≥97%，对齐行业头部水平 [(zvzo.com)](https://www.zvzo.com/2358/view-106620-1.html) ）三项核心指标，以数据驱动功能取舍。

---

## 12. 风险与挑战

**用户粘性风险（最高优先级）**：智能手表/手环约29–30%的弃用率 [(lmtw.com)](https://lmtw.com/mzw/content/detail/id/182768) 意味着每三个"手表钥匙用户"中就可能有一个人在一年后不再戴表。缓释策略是冗余体系（物理钥匙至少1把 + NFC 卡片 + 手机钥匙三层兜底）与"唤醒设计"（用车-表联动功能提升手表留存），并在用户研究中持续监测弃用趋势。

**安全与责任风险**：数字钥匙扩大攻击面（中继攻击、SE 侧信道、分享权限滥用），且当钥匙被滥用引发事故时，车主、车企、设备商、方案商之间的责任划分尚无法规定论 [(CSDN社区)](https://bbs.csdn.net/weixin_29901799/article/details/100158638) 。建议 UWB 安全测距 + SE 芯片存储 + 测距密钥短有效期 [(carconnectivity.org)](https://carconnectivity.org/wp-content/uploads/2022/12/CCC_Digital_Key_Whitepaper_Approved-3.0_v2-1.pdf) 的技术组合作为安全基线，并在用户协议与保险条款中前置约定。

**生态碎片化风险**：CCC、ICCE、ICCOA 多标准并行，华为/苹果/小米/OPPO 各生态的机型支持列表、iOS 配对限制、手环能力裁剪各不相同 [(Huawei Consumer)](https://consumer.huawei.com/cn/support/content/zh-cn15892299/) ，多头适配的测试与维护成本会随生态数量指数上升。建议通过标准化接入平台（Device HUB 类网关 [(腾讯云)](https://cloud.tencent.com/developer/article/2678004) ）收敛适配成本，并将兼容性矩阵作为发布物定期维护。

**成本下探与配置内卷风险**：UWB 正从30万元级向20万元以下快速下探 [(电子工程专辑 EE Times China)](https://www.eet-china.com/mp/a361225.html) ，若竞品在同价位标配 UWB 无感钥匙而本品牌缺席，将形成配置对比劣势；反之在低价位车型盲目上 UWB 又会侵蚀本已微薄的毛利。分层策略（第7.2节）需每半年按 BOM 降本曲线（国产 UWB 芯片量产驱动 [(电子工程专辑 EE Times China)](https://www.eet-china.com/mp/a361225.html) ）滚动校准。

---

## 13. 结论

智能穿戴替代物理车钥匙，本质上不是一次"设备替换"，而是**用车准入体系从"持有物认证"向"随身身份认证"的范式迁移**。对主机厂的核心建议可浓缩为五句话：**其一**，数字钥匙（BLE+NFC）应加速全系标配，这是降本与体验双赢的确定性投入；**其二**，UWB 按价格带分层配置，它解决的不是"能不能解锁"而是"无感体验的完整性与防中继的安全上限"；**其三**，手表钥匙的目标用户是存量可穿戴用户，打法是"收割已经戴表的人"而非"教育不戴表的人"，冗余体系永远不可省；**其四**，手表对手机的依赖设计决定迁移理由是否成立——近场必须独立、远程优先 eSIM、表端只做轻操作；**其五**，商业模式以品牌生态合作为主线，ODM/联名限定于营销与运营层，让用户的表成为车的钥匙，而不是让车企成为手表厂商。

---

*本报告基于公开资料与行业研究撰写，定性评估部分（雷达图评分、用户群体比例估算）为产品分析判断，供决策参考，不构成投资或法律建议。*

 [(CSDN社区)](https://bbs.csdn.net/weixin_29901799/article/details/100158638) : https://bbs.csdn.net/weixin_29901799/article/details/100158638
 [(腾讯云)](https://cloud.tencent.com/developer/article/2678004) : https://cloud.tencent.com/developer/article/2678004
 [(CSDN博客)](https://blog.csdn.net/weixin_30568591/article/details/96857092) : https://blog.csdn.net/weixin_30568591/article/details/96857092
 [(CSDN博客)](https://blog.csdn.net/weixin_28716443/article/details/160542184) : https://blog.csdn.net/weixin_28716443/article/details/160542184
 [(VicOne)](https://vicone.com/zh/blog/from-fob-to-phone-how-ccc-digital-key-40-shapes-automotive-cybersecurity/) : https://vicone.com/zh/blog/from-fob-to-phone-how-ccc-digital-key-40-shapes-automotive-cybersecurity/
 [(iotexpo.com.cn)](https://m.iotexpo.com.cn/SH/NewsView/2C3A3D63BACAAF75.html) : https://m.iotexpo.com.cn/SH/NewsView/2C3A3D63BACAAF75.html
 [(电子工程世界)](https://www.eeworld.com.cn/qcdz/eic693022.html) : https://www.eeworld.com.cn/qcdz/eic693022.html
 [(nextgen-technology.com)](https://resources.nextgen-technology.com/zh/ccc-digital-key-3-latest) : https://resources.nextgen-technology.com/zh/ccc-digital-key-3-latest
 [(jgvogel.cn)](https://file.jgvogel.cn/125/upload/resources/file/479607.pdf) : https://file.jgvogel.cn/125/upload/resources/file/479607.pdf
 [(小鹏汽车)](https://www.xiaopeng.com/news/company_news/5532.html) : https://www.xiaopeng.com/news/company_news/5532.html
 [(DevPress官方社区)](https://devpress.csdn.net/v1/article/detail/133095241) : https://devpress.csdn.net/v1/article/detail/133095241
 [(carconnectivity.org)](https://carconnectivity.org/wp-content/uploads/2022/12/CCC_Digital_Key_Whitepaper_Approved-3.0_v2-1.pdf) : https://carconnectivity.org/wp-content/uploads/2022/12/CCC_Digital_Key_Whitepaper_Approved-3.0_v2-1.pdf
 [(Huawei Consumer)](https://consumer.huawei.com/cn/support/content/zh-cn15999965/) : https://consumer.huawei.com/cn/support/content/zh-cn15999965/
 [(Huawei Consumer)](https://consumer.huawei.com/cn/support/content/zh-cn15892299/) : https://consumer.huawei.com/cn/support/content/zh-cn15892299/
 [(ZAKER)](https://app.myzaker.com/news/article.php?pk=6a50534f8e9f0946eb468831) : https://app.myzaker.com/news/article.php?pk=6a50534f8e9f0946eb468831
 [(爱思助手)](https://m.i4.cn/article/51966.html) : https://m.i4.cn/article/51966.html
 [(IT之家)](https://www.ithome.com/0/927/606.htm) : https://www.ithome.com/0/927/606.htm
 [(Huawei Consumer)](https://consumer.huawei.com/cn/support/content/zh-cn16029489/) : https://consumer.huawei.com/cn/support/content/zh-cn16029489/
 [(idc.com)](https://my.idc.com/getdoc.jsp?containerId=prCHC53244925) : https://my.idc.com/getdoc.jsp?containerId=prCHC53244925
 [(linktop.com.cn)](https://www.linktop.com.cn/yjzx/1-4082.html) : https://www.linktop.com.cn/yjzx/1-4082.html
 [(电子工程世界论坛)](https://bbs.eeworld.com.cn/thread-1295548-1-1.html) : https://bbs.eeworld.com.cn/thread-1295548-1-1.html
 [(bravechip.com)](http://www.bravechip.com/h-nd-20.html) : http://www.bravechip.com/h-nd-20.html
 [(微信公众平台)](http://mp.weixin.qq.com/s?__biz=MzI1MjkzMTcwOQ==&mid=2247642814&idx=5&sn=f3f63244262a1799a80b141eac2216b2) : http://mp.weixin.qq.com/s?__biz=MzI1MjkzMTcwOQ==&mid=2247642814&idx=5&sn=f3f63244262a1799a80b141eac2216b2
 [(世展网)](https://www.shifair.com/wap/article_details/index/id/102642.html) : https://www.shifair.com/wap/article_details/index/id/102642.html
 [(财联社)](https://www.cls.cn/detail/1090122) : https://www.cls.cn/detail/1090122
 [(电子工程专辑 EE Times China)](https://www.eet-china.com/mp/a361225.html) : https://www.eet-china.com/mp/a391950.html
 [(新京报)](https://m.bjnews.com.cn/detail/163533799714752.html) : https://m.bjnews.com.cn/detail/163533799714752.html
 [(Holafly eSIM)](https://esim.holafly.com/cn/blogs/apple-watch-esim-benefits/) : https://esim.holafly.com/cn/blogs/apple-watch-esim-benefits/
 [(什么值得买)](https://post.smzdm.com/p/a95edp50) : https://post.smzdm.com/p/a95edp50
 [(搜狐)](https://www.sohu.com/a/1016675222_121117455) : https://www.sohu.com/a/1016675222_121117455
 [(zvzo.com)](https://www.zvzo.com/2358/view-106620-1.html) : https://www.zvzo.com/2358/view-106620-1.html
 [(queniu.cn)](https://www.queniu.cn/post/27772.html) : https://www.queniu.cn/post/27772.html
 [(搜狐)](https://www.sohu.com/a/875657635_115931) : https://www.sohu.com/a/875657635_115931
 [(腾讯新闻)](https://new.qq.com/rain/a/20250318A07BSP00) : https://new.qq.com/rain/a/20250318A07BSP00
 [(phisemi.com)](https://www.phisemi.com/nd.jsp?id=81) : https://www.phisemi.com/nd.jsp?id=81
 [(xiouwang.cn)](https://xiouwang.cn/oarticle/articles/7423.html) : https://xiouwang.cn/oarticle/articles/7423.html
 [(sina.cn)](https://cj.sina.cn/articles/view/7857201856/1d45362c001903oth0?froms=ggmp) : https://cj.sina.cn/articles/view/7857201856/1d45362c001903oth0?froms=ggmp
 [(中金在线财经号)](http://mp.cnfol.com/56373/article/1785208258-142594861.html) : http://mp.cnfol.com/56373/article/1785208258-142594861.html
 [(中关村在线智能穿戴频道)](https://smartwear.zol.com.cn/1106/11064148.html) : https://smartwear.zol.com.cn/1106/11064148.html
 [(搜狐)](https://www.sohu.com/a/969792239_362225) : https://www.sohu.com/a/969792239_362225
 [(IT之家)](https://www.ithome.com/0/908/350.htm) : https://www.ithome.com/0/908/350.htm
 [(新浪)](https://k.sina.com.cn/article_7879995959_1d5af323706801trjg.html) : https://k.sina.com.cn/article_7879995959_1d5af323706801trjg.html
 [(icloudnews.net)](https://www.icloudnews.net/a/37710.html) : https://www.icloudnews.net/a/37710.html
 [(lmtw.com)](https://lmtw.com/mzw/content/detail/id/182768) : https://lmtw.com/mzw/content/detail/id/182768
 [(车家号)](https://chejiahao.m.autohome.com.cn/info/24497627) : https://chejiahao.m.autohome.com.cn/info/24497627
 [(36kr.com)](https://eu.36kr.com/zh/p/3629503396348935) : https://eu.36kr.com/zh/p/3629503396348935
