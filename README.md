# wordpress 主機推薦：先分清共享主機與三網優化 VPS，再決定要不要為了中國訪客自己維護

「wordpress 主機推薦」這個關鍵字的前排文章，大多在幫你比較 SiteGround、Hostinger、Cloudways 哪家方案便宜、後台好用、客服回得快。這些清單解決的是「我不想碰伺服器」這個需求，本身沒問題。

但如果你的卡點是另一件事——網站主要讀者在中國大陸，晚上八點到十一點連自己網站要等好幾秒——那些清單幫不上忙。問題出在回程線路，不在主機商後台按鈕夠不夠多。

GoMami（GoMami Networks, LLC）賣的是另一種東西：主打香港、日本、新加坡節點的中國三網優化回程（電信 CN2、聯通 AS9929、移動 CMIN2），加上高單核效能與最高 600Gbps 的 DDoS 清洗，最低 $29/月。它是不是你的答案，取決於你願意接手多少維護工作。

> **選購速覽**
> 想一鍵裝好 WordPress、不想碰 SSH：留在共享或託管主機，這篇看完知道差別就好。
> 主要訪客在中國大陸、在意晚高峰延遲、願意自己弄 LNMP 或裝控制面板：入門看 JPN Pulse Nano 或 SIN Pulse Nano（$29/月），要香港低延遲看 HKG Pulse Mini（$59/月），資料庫吃重的站看 HKG Turin Mini（$69/月）。
> 👉 [查看 GoMami 全系列套餐與目前價格](https://bit.ly/Gomami)

## 共享主機、託管主機、VPS 差在哪裡

差在誰負責維護作業系統和應用層，而這個差別直接決定「wordpress 主機推薦」清單裡哪些名字對你有意義。

共享主機是廠商把 PHP、資料庫、SSL、備份全部弄好，你只管後台發文；VPS 是給你一台虛擬機，裝什麼系統、用哪個 PHP 版本、資料庫被掃爆誰修，都是你。託管主機介於兩者之間，廠商多扛一些維運，價格也高一階。

這條分界線決定了我們怎麼推薦。SiteGround 的 StartUp 方案首年 $2.99/月、續約 $17.99/月（12 個月預付），限時含免費網域與免費遷站，另有 30 天退款保障；Hostinger 的入門 KVM 方案約 $4.99/月，1 vCPU / 4GB / 50GB NVMe / 1TB 流量。兩者都是「付錢省事」的解法，機房在歐美或新加坡，沒有針對中國大陸的精品回程。

GoMami 這類非託管 VPS 走的是相反路線：把成本花在線路和硬體上，把維護責任交回你手上。同價位帶你在共享主機買到的是「有人幫你顧」，在 GoMami 買到的是一台線路很好的空機，環境得自己搭——官方文件沒有 WordPress 一鍵安裝這回事。

| 方案類型 | 例子 | 價格帶 | 環境誰維護 | 中國線路優化 |
| --- | --- | --- | --- | --- |
| 共享／託管主機 | SiteGround StartUp | 首年 $2.99/月，續約 $17.99/月 | 廠商 | 無專門優化 |
| 入門 VPS | Hostinger KVM 1 | 約 $4.99/月 | 自己 | 無專門優化 |
| 中國優化 VPS | GoMami JPN Pulse Nano | $29/月起 | 自己 | CN2 / 9929 / CMIN2 |

（競品價格為撰文時公開資訊，僅供對照，實際以各家結帳頁為準。）

## WordPress 為什麼特別吃「線路」這一項

因為 WordPress 每次頁面請求都要跑一輪 PHP 模板邏輯加數十次資料庫查詢，伺服器端處理完才吐出第一個位元組；這段等待叫 TTFB，它由單核效能和磁碟 I/O 決定，而從使用者點擊到伺服器開始回應的那段空窗期，由線路延遲決定。

對中文訪客為主的站，線路的權重往往高過 CPU。走普通 163 骨幹的線路，晚高峰一塞，延遲可以從 40ms 飆到 200ms 以上，TCP 握手要多等好幾輪，後台登入都會轉圈。CN2 GIA、AS9929、CMIN2 這三條精品線路的作用，就是把這段延遲壓回可控範圍。三條線分別對應三家電信業者：

| 線路代號 | 對應電信業者 | 中國往日本方向大致延遲 |
| --- | --- | --- |
| CN2 GIA | 中國電信 | 約 40–55ms |
| AS9929 | 中國聯通 | 約 45–65ms |
| CMIN2 | 中國移動 | 約 40–60ms |

GoMami 的做法是三網回程各走各家精品線，官方標示中國大陸 RTT 可低於 50ms。

## GoMami 的產品線與明確不適合的人

官方文件把產品線分成三條：Turin 是效能旗艦（香港，最新一代硬體）、Pulse 是均衡系列（香港、日本、新加坡三地）、Forge 是香港的獨享伺服器（EPYC 7663、56 核 112 執行緒、128GB 記憶體起）。官網 Global PoPs 只列香港、日本、新加坡三地。

洛杉磯的 LAX Pulse 系列目前在商店頁和第三方庫存監測裡看得到、全部有貨，但官方文件尚未收錄，長期供應狀況要自己評估。另外提醒一件容易搞混的事：gomamihosting.com 是另一個完全不同的站，跟 gomami.io 沒有關係。

**不適合找 GoMami 的人**：月預算 $5 以內、希望廠商幫你排查外掛衝突、需要 cPanel 和主機信箱、訪客主要在歐美。**適合的人**：訪客在中國大陸、能接受自己顧一台 Linux、對晚高峰延遲有明確要求。

## 全套餐與價格

以下價格為月付、美元，整理自官網商店配置頁、首頁方案卡與第三方庫存監測（2026 年 8 月快照）。**下單前請在購物車核對實際金額**，原因見後面「價格對不上」那一段。

### 香港：HKG Turin 與 HKG Pulse

| 套餐 | vCPU / 記憶體 / NVMe | 月流量 / 頻寬 | 月價 | 購買 |
| --- | --- | --- | --- | --- |
| HKG.Turin.Mini | 2 / 4GB / 100GB | 1TB / 2Gbps | $69 | [ 選 Turin Mini](https://gomami.io/aff.php?aff=415&pid=14) |
| HKG.Turin.Air | 4 / 8GB / 140GB | 2TB / 2Gbps | $129 | [ 選 Turin Air](https://gomami.io/aff.php?aff=415&pid=15) |
| HKG.Turin.Pro | 6 / 16GB / 180GB | 5TB / 5Gbps | $299 | [ 選 Turin Pro](https://gomami.io/aff.php?aff=415&pid=16) |
| HKG.Turin.Ultra | 12 / 32GB / 220GB | 10TB / 5Gbps | $599 | [ 選 Turin Ultra](https://gomami.io/aff.php?aff=415&pid=22) |
| HKG.Pulse.Nano | 2 / 2GB / 40GB | 500GB / 1Gbps | $49 | [ 選 Pulse Nano](https://gomami.io/aff.php?aff=415&pid=26) |
| HKG.Pulse.Mini | 2 / 4GB / 60GB | 1TB / 1Gbps | $59 | [ 選 Pulse Mini](https://gomami.io/aff.php?aff=415&pid=4) |
| HKG.Pulse.Air | 4 / 8GB / 80GB | 2TB / 1Gbps | $119 | [ 選 Pulse Air](https://gomami.io/aff.php?aff=415&pid=5) |
| HKG.Pulse.Pro | 8 / 16GB / 100GB | 5TB / 3Gbps | $269 | [ 選 Pulse Pro](https://gomami.io/aff.php?aff=415&pid=6) |
| HKG.Pulse.Ultra | 16 / 32GB / 300GB | 10TB / 5Gbps | $499 | [ 選 Pulse Ultra](https://gomami.io/aff.php?aff=415&pid=25) |

Turin 系列搭載 AMD EPYC 9575F（Zen 5），第三方實測 HKG.Turin.Mini 的 Geekbench 5 單核 2259、多核 4262，fio 1M 區塊讀 3.88GB/s、寫 4.14GB/s。Pulse 系列在香港為 EPYC 7763。

### 香港：Peak X5 與 Forge

| 套餐 | vCPU / 記憶體 / NVMe | 月流量 / 頻寬 | 月價 | 購買 |
| --- | --- | --- | --- | --- |
| HKG.Peak.X5.Mini | 2 / 4GB / 40GB | 1TB / 2Gbps | $59 | [ 查看 Peak X5 系列](https://bit.ly/Gomami) |
| HKG.Peak.X5.Air | 4 / 8GB / 60GB | 2TB / 2Gbps | $99 | [ 查看 Peak X5 系列](https://bit.ly/Gomami) |
| HKG.Peak.X5.Pro | 6 / 16GB / 80GB | 5TB / 5Gbps | $199 | [ 查看 Peak X5 系列](https://bit.ly/Gomami) |
| HKG.Forge.Mini | 56C/112T / 128GB / 960GB | 10TB / 2Gbps | $599 | [ 查看 Forge 獨享伺服器](https://bit.ly/Gomami) |
| HKG.Forge.Air | 56C/112T / 256GB / 4TB | 20TB / 2Gbps | $899 | [ 查看 Forge 獨享伺服器](https://bit.ly/Gomami) |

Peak X5 用 Ryzen 9 9950X（最高 5.7GHz），價格取自官網首頁方案卡。Forge 系列走 TYAN B8033 平台，付款後即時開通，額外 IP 每個 $10、每台最多 4 個，超流量按 $0.06/GB 計費而非限速。

### 日本與新加坡：JPN Pulse、SIN Pulse

| 套餐 | vCPU / 記憶體 / NVMe | 月流量 / 頻寬 | 月價 | 購買 |
| --- | --- | --- | --- | --- |
| JPN.Pulse.Nano | 2 / 2GB / 40GB | 500GB / 1Gbps | $29 | [ 選 JPN Pulse Nano](https://gomami.io/aff.php?aff=415&pid=13) |
| JPN.Pulse.Mini | 2 / 4GB / 60GB | 1TB / 1.5Gbps | $49 | [ 選 JPN Pulse Mini](https://gomami.io/aff.php?aff=415&pid=10) |
| JPN.Pulse.Air | 4 / 8GB / 80GB | 2TB / 1Gbps | $89 | [ 選 JPN Pulse Air](https://gomami.io/aff.php?aff=415&pid=11) |
| JPN.Pulse.Pro | 8 / 16GB / 100GB | 5TB / 3Gbps | $169 | [ 選 JPN Pulse Pro](https://gomami.io/aff.php?aff=415&pid=12) |
| JPN.Pulse.Ultra | 12 / 32GB / 300GB | 10TB / 3Gbps | $338 | [ 選 JPN Pulse Ultra](https://gomami.io/aff.php?aff=415&pid=24) |
| SIN.Pulse.Nano | 2 / 2GB / 40GB | 500GB / 1Gbps | $29 | [ 選 SIN Pulse Nano](https://gomami.io/aff.php?aff=415&pid=21) |
| SIN.Pulse.Mini | 2 / 4GB / 60GB | 1TB / 1Gbps | $49 | [ 選 SIN Pulse Mini](https://gomami.io/aff.php?aff=415&pid=17) |
| SIN.Pulse.Air | 4 / 8GB / 80GB | 2TB / 1Gbps | $89 | [ 選 SIN Pulse Air](https://gomami.io/aff.php?aff=415&pid=18) |
| SIN.Pulse.Pro | 8 / 16GB / 100GB | 5TB / 3Gbps | $169 | [ 選 SIN Pulse Pro](https://gomami.io/aff.php?aff=415&pid=19) |
| SIN.Pulse.Ultra | 12 / 32GB / 300GB | 10TB / 5Gbps | $338 | [ 選 SIN Pulse Ultra](https://gomami.io/aff.php?aff=415&pid=23) |

### 洛杉磯：LAX Pulse

| 套餐 | vCPU / 記憶體 / NVMe | 月流量 / 頻寬 | 月價 | 購買 |
| --- | --- | --- | --- | --- |
| LAX.Pulse.Nano | 2 / 2GB / 40GB | 1TB / 1Gbps | $29 | [ 選 LAX Pulse Nano](https://gomami.io/aff.php?aff=415&pid=27) |
| LAX.Pulse.Mini | 2 / 4GB / 60GB | 2TB / 1Gbps | $59 | [ 選 LAX Pulse Mini](https://gomami.io/aff.php?aff=415&pid=28) |
| LAX.Pulse.Air | 4 / 8GB / 80GB | 4TB / 2Gbps | $129 | [ 選 LAX Pulse Air](https://gomami.io/aff.php?aff=415&pid=29) |
| LAX.Pulse.Pro | 6 / 16GB / 100GB | 8TB / 3Gbps | $259 | [ 選 LAX Pulse Pro](https://gomami.io/aff.php?aff=415&pid=30) |
| LAX.Pulse.Ultra | 12 / 32GB / 300GB | 15TB / 5Gbps | $599 | [ 選 LAX Pulse Ultra](https://gomami.io/aff.php?aff=415&pid=31) |
| LAX.Pulse.Titan | 12 / 32GB / 600GB | 30TB / 10Gbps | $999 | [ 選 LAX Pulse Titan](https://gomami.io/aff.php?aff=415&pid=32) |

同樣的規格，LAX 給的流量大約是香港的兩倍。圖片多、影片多的站，這個差別在帳單上很具體。

## 機房怎麼選：先看你的訪客用哪家電信

答案不是「香港最好」，而是看訪客的電信業者比例。第三方在 2025 年 12 月對 HKG.Turin.Mini、JPN.Pulse.Nano、SIN.Pulse.Mini 做過完整實測，結論有明顯分化：

| 訪客主要電信業者 | 建議排序 | 實測狀況 |
| --- | --- | --- |
| 中國電信 | 香港 ≈ 日本 > 新加坡 | 三地都穩，單線程 400Mbps 以上 |
| 中國聯通 | 香港 > 日本 > 新加坡 | 聯通拉新加坡上行斷流較嚴重 |
| 中國移動 | 新加坡 > 日本 ≈ 香港 | 港日上行被 QoS，下行正常 |

具體到數字：深圳電信（500Mbps）拉到 HKG.Turin.Mini 單線程約 475Mbps，濟南聯通約 545–571Mbps。廣東移動拉到香港，上行 30 秒平均只有 38Mbps，下行還是有 284Mbps；武漢、寧波的移動下行能到 549–653Mbps。日本方向類似，電信 404–417Mbps、聯通 358–545Mbps，移動上行同樣被壓。

對建站來說，上行被 QoS 影響不大，因為訪客主要在下載你的頁面。但如果你打算拿這台機器做直播推流、大量上傳備份，移動線路的體驗要打折。

## 下單前一定要知道的三件事

第一件：**流量用完不會停機，會被限速到 20KB/s**，一直持續到下個計費週期。這個速度基本上等於網站癱瘓，比直接停機更難察覺。可以加購流量包（100GB $6、1TB $60、10TB $600、20TB $1,200），但**只在當期有效、不結轉到下個月**。Forge 系列例外，按 $0.06/GB 超量計費。

第二件：**24 小時無理由退款只限首次購買，每人一次，續約訂單不退**。支付寶退款 1–3 個工作日、信用卡 5–10 個工作日、加密貨幣 1–3 個工作日。超過 24 小時、違反 ToS、動用過的帳戶餘額、因 DDoS 導致 IP 被牽引，都不退。退款通過後執行個體和資料立即刪除。

這意味著「先開一台測線路，不滿意再開一台」的玩法只有一次機會。要測就把 ping、traceroute、iperf3、實際頁面載入一次測完。順帶一提，5201 這個 iperf3 預設埠在香港節點是被屏蔽的，測速要換埠。

第三件：**官網首頁的方案卡價格，跟商店和第三方監測對不上**。首頁用 EPYC 7763 的機型標的是 $39 / $79 / $169，但商店配置頁與第三方庫存監測（2026 年 8 月 21 日核對）給出的 HKG Pulse 是 $59 / $119 / $269。首頁那張卡只標 CPU 不標系列名，無法確認對應哪條產品線。**一律以購物車結算頁為準**。

另外翻一下 ToS：明確禁止 botting，尤其針對 TikTok 等平台的自動化操作，違規直接終止帳戶且不退款。做採集、刷量類站點的人要先看清楚。

## 優惠碼怎麼用

目前有兩個可查證的碼。`GOMAMI365` 是全線 8 折、循環優惠，續費同價，Forge 系列不參與；`Hi,LAX` 是 LAX 系列首發 8 折、限時。在購物車頁面的 Promo Code 欄位填入即可，疊加規則請在結帳頁確認。

按 8 折換算（非官方標價，僅供估算）：JPN Pulse Nano $29 → $23.2/月、SIN Pulse Mini $49 → $39.2/月、HKG Pulse Mini $59 → $47.2/月、HKG Turin Mini $69 → $55.2/月、HKG Peak X5 Pro $199 → $159.2/月。

如果你只是想先確認線路對不對，用最便宜的 $29 方案加 8 折開一台來測，成本比直接上年付低很多。

👉 [用 GOMAMI365 開一台 JPN Pulse Nano 測線路](https://gomami.io/aff.php?aff=415&pid=13)

## 從開機到 WordPress 上線，實際上要做這些

流程不複雜，但每一步都是你自己動手。付款後系統幾分鐘內自動部署，IP 和登入憑證寄到信箱。

1. **選系統**：Debian 12 或 Ubuntu 22.04 / 24.04，社群文件和排錯資料最齊。
2. **建環境**：想乾淨就手動搭 Nginx + PHP-FPM + MariaDB；不想折騰就用 WordOps、CyberPanel、HestiaCP 這類面板，大約十分鐘能跑起來。
3. **上快取**：Redis 或 Memcached 做物件快取，配合 LiteSpeed Cache 或 WP Rocket 做頁面快取。NVMe 的 IOPS 充足，資料庫快取命中率會比共享主機高。
4. **自己做安全**：fail2ban 防爆破、SSH 改金鑰登入、後台兩步驗證、WAF 外掛。L3/L4 的 DDoS 由 GoMami 的清洗兜底，應用層要自己顧。
5. **自己做備份**：非託管方案沒有幫你備份網站的義務，備份排程和外存位置都要自己規劃。

控制台有幾個實用設定：面板可以即時查看 CPU、記憶體和網路流量，被流量或爬蟲打的時候不用 SSH 進去猜；改 hostname 只會改面板顯示名，要同步系統 hostname 得 SSH 執行 `hostnamectl`；開機順序可以切到 CD-ROM 掛 ISO 裝自訂系統，裝完記得改回硬碟；系統隨時可從面板重裝。

👉 [選好機房與方案後直接在購物車結帳](https://gomami.io/aff.php?aff=415&pid=4)

## 一年到底花多少：跟共享主機算一次總成本

以最低配置比：GoMami JPN Pulse Nano 月付 $29，一年 $348；用 `GOMAMI365` 8 折後約 $23.2/月，一年約 $278（按折後月價乘以 12 換算，非官方年付標價）。

對照 SiteGround StartUp：首年 $2.99/月，12 個月預付共 $35.88；但那是首購促銷價，**續約價 $17.99/月是從第二個計費期才生效**，換算下來第二年 $215.88。也就是說，第一年差距是 $348 對 $35.88（將近十倍），第二年縮到 $348 對 $215.88（約 1.6 倍）。拿首年促銷價當長期成本基準，會嚴重低估共享主機的實際支出。Hostinger 入門 KVM 約 $4.99/月，一年不到 $60，同樣要看續約條款。

即使按續約價對比，GoMami 仍貴一些，差額換到的是三網精品回程和那顆 Zen 5／EPYC 的單核效能。

值不值得，取決於你原來那台機器到底卡在哪。SiteGround 自己公布的遷移實測顯示，WordPress 站遷入後 TTFB 中位數落在 284–315ms，對照組 Bluehost 915.5ms、Hostinger 786.5ms。這組數字是歐美量測基線，不能直接換算成中國訪客的體驗，但它說明共享主機的 TTFB 本來就是兩三百毫秒的量級——再加上跨境線路在晚高峰的抖動，才是你晚上開站轉圈的原因。

反過來說，如果你訪客九成在台灣或歐美，花 $29 買中國三網優化是浪費。$4.99 的入門 VPS 或首年 $2.99 的共享主機方案，對你更划算。

## 常見問題

**GoMami 可以一鍵安裝 WordPress 嗎？**
不行。官方文件沒有這項功能，它是非託管 VPS，環境要自己搭或用第三方面板。

**流量用完會直接停機嗎？**
不會停機，限速到 20KB/s 直到下個計費週期。這個速度實務上等於不能用，選套餐時流量留 20% 餘量比較安全。

**支援支付寶嗎？**
官方退款時限表列出支付寶（1–3 個工作日），第三方說明也提到信用卡、Stripe、加密貨幣。實際可用選項請在結帳頁確認。

**為什麼官網首頁的價格跟結帳頁不一樣？**
首頁方案卡只標 CPU 型號、不標系列，與商店配置頁對不上。以購物車金額為準。

**適合跑 WooCommerce 嗎？**
硬體綽綽有餘，但金流、外掛、備份、資安全是你的事。流量按單向計算（只算流出），商品圖多的站要留意月流量。

**JPN 和 SIN 的線路跟香港一樣嗎？**
同樣是 CN2 / 9929 / CMIN2 三網回程，但實際體驗看電信業者。聯通到新加坡上行容易斷流，移動到香港與日本上行被 QoS，這兩點在第三方實測裡都有數據。

## 最後，按你的情況選

只想盡快上線、不碰伺服器：留在共享主機，SiteGround 首年 $2.99/月（第二年續約 $17.99/月）或 Hostinger 入門 KVM 約 $4.99/月，都比自己顧一台機器省事。

訪客在中國大陸、願意維護：先用 $29 的 JPN Pulse Nano 或 SIN Pulse Nano 加 8 折碼測線路，24 小時內把 ping、路由、實際頁面載入測完。

確定要香港低延遲：小型站 HKG Pulse Mini $59，資料庫查詢吃重的站上 HKG Turin Mini $69，Turin 的 Zen 5 單核與 NVMe 隨機讀寫在資料庫場景差距明顯。

多站、重型業務：Turin Air 以上，或直接看 Forge 的 128GB 獨享方案。

下單前做兩件事：在購物車核對實際金額（首頁價不可信），以及確認你要測的線路在 24 小時退款窗口內一次測完——那個窗口只有一次。

👉 [前往 GoMami 挑選適合你的方案](https://bit.ly/Gomami)
