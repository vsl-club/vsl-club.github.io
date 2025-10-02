---
title: 'Nhập môn Khai thác ứng dụng Web (Web Exploitation)'
description: "Nhập môn Khai thác ứng dụng Web (Web Exploitation)"
date: 2025-10-02 15:43:03
tags:
  - Knowledge
  - Web
author:
  - armymen
  - d4kw1n
top_img: /img/training/web.png
cover: /img/training/web.png
category: 
  - 'Knowledge'
  - 'Web'
---

# WEB — Giới thiệu nhanh & Roadmap Web Exploitation

Xin chào các đạo hữu tương lai của **Hắc Đạo**! 👋

Như đã thông báo, series này chia sẻ hành trình và kinh nghiệm trên con đường **Web Security**. Hy vọng roadmap này sẽ giúp các bạn đang bế tắc hoặc lạc lối đặt viên gạch đầu tiên trên con đường tu luyện.

> Web là mảng dễ tiếp cận nhất trong CTF — nhưng để đi thật sâu bạn cần rất nhiều thời gian và thực hành. Càng đi sâu, càng thấy rộng và rối — chuẩn "phễu ngược". Hãy kiên nhẫn, vui vẻ và tìm đồng đội tốt để cùng nhau tiến.

---

## Cảm giác khi học Web

Bạn sẽ trải qua thời kỳ hưng phấn lúc mới bắt đầu, rồi có thể rơi vào **Thung lũng Tuyệt Vọng** khi gặp lỗi khó, nhưng rồi sẽ vượt qua khi có trải nghiệm và đồng đội.

---

## [Beginner Level] — Bắt đầu như thế nào?

### 1. LẬP TRÌNH, LẬP TRÌNH và LẬP TRÌNH

Cái gì quan trọng thì nhắc lại 3 lần — lập trình là nền tảng. Không cần trở thành dev chuyên sâu, nhưng phải đọc/viết/debug code ở mức **basic → medium**.

**Ngôn ngữ nên học**

* **Python** — scripting, automation, exploit scripts (Flask/Django hiểu server side).
* **JavaScript** — client-side, hiểu DOM, XSS, CORS, SPA (React, Vue, Node).
* **PHP** — nhiều ứng dụng web truyền thống dùng PHP (vulnerable apps thường viết bằng PHP).
* **Golang / Java / Rust / C#** — tốt để hiểu backend/thiết kế service khác nhau.

**Lợi ích của lập trình**

* Đọc hiểu luồng dữ liệu trên server.
* Viết script khai thác (kỹ năng bắt buộc).
* Dựng lại lỗi/vulnerable apps để hiểu root cause và cách vá.

---

### 2. Các lỗ hổng bảo mật cơ bản cần nắm

Giai đoạn đầu, tập trung vào **Server-side** trước, sau đó bổ sung **Client-side**.

**Server-side (ưu tiên)**

* **SQL Injection (SQLi)** — tìm, exploit, bypass filters, stacked queries, blind SQLi.
* **Command Injection** — exec hệ thống từ input (dangerous).
* **Path Traversal / LFI / RFI** — truy cập file hệ thống, include file độc hại.
* **File Upload** — bypass mime checks, upload webshell.
* **SSRF** — server request forgery (internal network scanning).
* **Authentication / Authorization flaws**: IDOR, broken auth, session fixation.

**Client-side**

* **XSS (Reflected / Stored / DOM)** — học cách exploit, chaining tới CSRF/stealing cookies.
* **CSP, CORS pitfalls** — misconfigurations that leak data.

**Các lỗ hổng khác quan trọng**

* **SSTI** (Server-Side Template Injection) — điều khiển template engine.
* **Insecure deserialization** — remote code exec danger.
* **Business logic flaws** — logic errors, rate limit bypass, purchase flow abuse.

---

### Quy trình học cho mỗi lỗ hổng (recommended)

1. **Học lý thuyết** (OWASP, PortSwigger Academy).
2. **Làm lab** bằng Burp Suite/Browser proxy.
3. **Viết script** (Python) để tự động solve/scan.
4. **Dựng lại vulnerable app** (simple Flask/PHP app) và vá để hiểu root cause.

---

## Tools thiết yếu

* **Burp Suite (Community/Pro)** — proxy, repeater, intruder, extender; bắt buộc.
* **OWASP ZAP** — alternative proxy scanner.
* **Browser DevTools** — network, console, storage, cookies.
* **sqlmap** — automated SQLi exploitation (but biết manual là quan trọng).
* **ffuf / dirb / gobuster** — web fuzzing & directory discovery.
* **Nikto** — basic web scanner.
* **nmap** — port/service discovery.
* **Hydra, Burp Intruder** — brute-force auth.
* **Metasploit** (khi cần) — exploit frameworks.
* **CyberChef** — decode/transform quick tasks.
* **Proxy tools & extensions**: Postman, REST client.
* **Burp extensions**: Autorize, Collaborator client, Logger++, etc.

---

## Cách tiếp cận: manual trước, automated sau

* Luôn hiểu kỹ bước tấn công **bằng tay** (Burp Repeater).
* Sau khi hiểu rõ, tự động hoá với script/sqlmap/ffuf.
* Viết script giúp tái sử dụng và scale scanning khi cần.

---

## Nơi luyện tập & labs

* **PortSwigger Web Security Academy** — lý thuyết + labs (bắt buộc).
* **TryHackMe (Web rooms)** — guided labs cho người mới.
* **HackTheBox (web challenges & machines)** — practice nâng cao.
* **OWASP Juice Shop** — vulnerable modern webapp.
* **Damn Vulnerable Web App (DVWA)**, **bWAPP** — classic vulnerable apps.
* **Root Me (Web challenges)** — nhiều thể loại.
* **CTFtime / past CTF writeups** — đọc writeups để học patterns.

---

## Roadmap học gợi ý (tuần/tháng)

**Tuần 0–2 — Khởi động & Công cụ**

* Cài Burp Suite, browser proxy, ffuf, sqlmap.
* PortSwigger: hoàn thành các bài Intro (Injection, XSS cơ bản).

**Tuần 3–6 — Server-side fundamentals**

* Học SQLi (union, blind, time-based), Command Injection, LFI/RFI, File Upload.
* Làm lab trên PortSwigger + DVWA + Juice Shop.
* Viết script exploit đơn giản (Python + requests).

**Tuần 7–10 — Client-side & chaining**

* XSS nâng cao, CSP, DOM XSS.
* SSTI, SSRF cơ bản.
* Học cách chain: XSS → CSRF → RCE (khi có thể).

**Tháng 3–6 — Automation & advanced**

* Recon tự động (ffuf, dirsearch), scanner tuning, Burp extensions.
* Business logic flaws, auth bypass, JWT issues, race conditions.
* Tham gia HTB/THM/CTF để thực chiến.

---

## Mẹo thực chiến & checklist khi gặp bài Web

1. **Đọc kỹ đề / source nếu có**: API docs, JS file, robots.txt có thể tiết lộ.
2. **Thu thập thông tin**: endpoints, parameters, cookies, headers.
3. **Thử manual payloads**: basic payloads cho SQLi/XSS/LFI.
4. **Xác định điểm tấn công**: input point => reflect/store/DB interaction/file include.
5. **Log & reproduce**: mọi bước phải reproducible (gõ script sau).
6. **Chain vulnerabilities**: nhiều CTF web cần chain nhiều lỗi nhỏ để đạt RCE/flag.
7. **Tôn trọng rules**: trên nền tảng luyện tập làm trong môi trường lab; thật sự tấn công site ngoài phạm vi là illegal.

---

## Công cụ & snippet hữu ích (quick cheatsheet)

* Burp Repeater: thử request → sửa param → resend.
* Burp Intruder / ffuf: fuzz parameter / directories.
* sqlmap --level=5 --risk=3 -u "http://..." --data="..."
* ffuf -u [http://site/FUZZ](http://site/FUZZ) -w wordlist.txt
* curl -v -X POST -d "username=...&password=..." http://...
* Python requests snippet để auto post/get: `requests.post(url, data=payload)`.

---

## Nguồn tài liệu & sách nên đọc

* **PortSwigger Web Security Academy** (free).
* **The Web Application Hacker's Handbook** — tác phẩm kinh điển.
* **Real-World Bug Hunting** — practical bug bounties.
* **OWASP Top 10 & ASVS** — biết các category và risk.
* Blogs & writeups: PortSwigger blog, HackerOne writeups, team CTF writeups.

---

## Văn hoá & tinh thần khi học Web

* Hỏi khi gặp khó — trong team hoặc community.
* Viết writeups để củng cố hiểu biết & chia sẻ với team.
* "Want to go fast? go alone. Want to go far? go together." — tìm đồng đạo để cùng tiến.

---
