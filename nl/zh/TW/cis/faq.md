---
copyright:
  years: 2018
lastupdated: "2018-28-03"
---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}

# 常見問題

## 如何使用「早期存取方案」？
「早期存取方案」是刻意設計成只容許一個帳戶有一個區域。建議每個帳戶只能建立一個實例，並驗證區域名稱。必須先驗證區域名稱，再新增區域名稱。如果刪除區域，則無法在「早期存取方案」期間新增另一個區域或相同區域。

## 為什麼我的網域處於「擱置」狀態？如何啟動它？
將網域新增至 CIS 時，我們為您提供數個名稱伺服器，以在您的登記員（或在 DNS 提供者上，如果您要新增子網域的話）處進行配置。除非您正確地配置名稱伺服器，否則網域或子網域會維持擱置狀態。請確定您將這兩個名稱伺服器新增至您的登記員或 DNS 提供者。我們會定期掃描公用 DNS 系統，以檢查是否已依指示配置名稱伺服器。只要可以驗證名稱伺服器變更（這最多可能需要 24 小時），就可以啟動您的網域。您可以按一下概觀頁面中的**重新檢查名稱伺服器**，來提交名稱伺服器重新檢查要求。

## 誰是網域的登記員？
如需此資訊，請參閱 https://whois.icann.org/。**附註**：當您將網域新增至 CIS 時，必須具有管理專用權才能編輯登記員處的網域配置，以更新或新增針對網域所提供的名稱伺服器。如果您不知道誰是您嘗試新增至 CIS 之網域的登記員，則不可能有權更新登記員的網域配置。請與您組織中網域的擁有者合作，以進行必要的變更。

## 我想要保留網域 (example.com) 的現行 DNS 提供者。我可以將現行 DNS 提供者的子網域 (subdomain.example.com) 委派給 CIS 嗎？
可以。此處理程序與新增網域類似，但您是與較高層次網域的 DNS 提供者合作，而不是與登記員合作。將子網域新增至 CIS 時，通常會提供兩個名稱伺服器供您進行配置。您可以將兩個名稱伺服器的「名稱伺服器 (NS)」記錄，配置為其他 DNS 提供者所管理之網域內的 DNS 記錄。當我們可以驗證已新增必要的 NS 記錄時，即會啟動您的子網域。如果您未管理組織內較高層次的網域，則必須與較高層次網域的擁有者合作來新增 NS 記錄。

## 何謂 TLS？
TLS 是一種標準安全通訊協定，用於在進行線上通訊的 Web 伺服器與瀏覽器之間建立加密鏈結。需要有 TLS 憑證才能建立與網站的 TLS 連線，而且它包含網域名稱、公司名稱及其他資料，例如公司地址、城市、州/省及國家/地區。憑證也會顯示到期日，以及發證之「憑證管理中心 (CA)」的詳細資料。

## TLS 如何運作？
瀏覽器起始與 TLS 安全網站的連線時，會先擷取網站的「TLS 憑證」，以檢查憑證是否仍然有效。它會驗證 CA 是否為瀏覽器所信任的 CA，以及發出此憑證的網站是否正在使用憑證。如果其中有任何檢查失敗，則您會看到警告，指出網站未受到有效憑證的保護。

在 Web 伺服器上安裝 TLS 憑證時，會啟用 Web 伺服器與與其連接之瀏覽器間的安全連線。網站的 URL 字首為 "https"，而不是 "http"，而小鎖會顯示在位址列上。如果網站使用延伸驗證 (EV) 憑證，則瀏覽器可能也會顯示綠色位址列。

## 為何會看到隱私權警告？
IBM Cloud CIS 所發出的 TLS 憑證涵蓋根網域 (`example.com`) 及一個層次的子網域 (`*.example.com`)。如果您嘗試到達第二層子網域 (`*.*.example.com`)，則會在瀏覽器中看到隱私權警告，因為這些主機名稱不會新增至 SAN。

也請容許最多 15 分鐘，讓我們的其中一個夥伴「憑證管理中心 (CA)」來發出新憑證。如果尚未發出新憑證，則您會在瀏覽器中看到隱私權警告。

## 何謂 DDoS？
分散式拒絕服務 (DDoS) 攻擊會利用來自多個來源的資料流量，嘗試讓線上服務而無法使用。在 DDoS 攻擊中，有多個受損的電腦系統會攻擊目標，例如伺服器、網站或其他網路資源，而這會影響目標資源的使用者。

進入目標系統的大量送入訊息、連線要求或形態異常的封包會強制它變慢，甚至損毀及關閉，進而拒絕服務合法使用者或系統。DDoS 攻擊已由各式各樣的威脅動作者執行，範圍包含個別犯罪駭客到組織犯罪環及政府機構。

## 我受到 DDoS 攻擊時怎麼辦？

**步驟 1：**在**概觀**畫面中，開啟「防禦模式」。 

![防禦模式](images/defense-mode.png)

**步驟 2：**設定 DNS 記錄以達到最高安全。

**步驟 3：**請不要對來自 IBM CIS 的要求進行速率限制或節流控制，我們需要頻寬來協助處理您的狀況。

**步驟 4：**必要的話，請封鎖特定國家/地區及訪客。

## 我收到 522 錯誤，該如何做？

522 錯誤指出無法建立與原點伺服器（即主機）的連線。大約 15 秒無法連接之後，我們會關閉連線，並顯示 522 錯誤頁面。

此問題通常是由意外封鎖 IP 位址的防火牆或安全軟體所造成。因為 CIS 作為反向 Proxy，所以您網站的連線會顯示為來自某範圍的 CIS IP。這種行為可能會導致某些防火牆封鎖這些連線，從而讓我們無法適當地將內容提供給網站造訪者。

若要修正此問題，請要求您的主機將所有 CIS IP 範圍列入白名單（即列在[這裡](whitelisted-ips.html)）。

所有這些 IP 都必須列入白名單，才能避免 522 錯誤。也可以查看是否封鎖這些範圍中的任何 IP。

522 錯誤也可能是網路連線問題所引起，因此請確認伺服器及網路的性能良好且未超載。

採取上述步驟之後，如果仍然收到錯誤，則請聯絡 IBM CIS 支援，並確認下列各項：

* 已將您列入我們 IP 範圍的白名單
* 您的伺服器/網路上線且性能良好

如果您聯絡我們的支援團隊，請提供最近 522 錯誤中的 Ray ID。我們可以使用此項目來判定您已命中的「CIS 資料中心」，並執行進一步測試。

## 何謂 Proxy 記錄以及需要它們的原因？

Proxy 記錄是透過 IBM CIS 對其資料流量進行 Proxy 處理的記錄。只有 Proxy 記錄才會接收 CIS 權益（例如 IP 遮罩），其中 CIS IP 會替換為您的原點 IP 來進行保護：

```
$ whois 104.28.22.57 | grep OrgName
OrgName:        IBM
```

如果您要在網域上略過 CIS（仍會解析 DNS），則對記錄進行非 Proxy 處理是可能的解決方案。

## 我收到「DNS 驗證」錯誤：1004；該如何做？

若要讓頁面規則運作，需要解析您區域的 DNS。因此，您必須有區域的 Proxy DNS 記錄。 
