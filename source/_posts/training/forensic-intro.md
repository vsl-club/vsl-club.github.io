---
title: 'Nhập môn Điều tra số (Digital Forensics)'
description: "Nhập môn Điều tra số (Digital Forensics)"
date: 2025-10-02 15:43:03
tags:
  - Knowledge
  - Digital Forensics
author:
  - armymen
  - d4kw1n
top_img: /img/training/forensic.png
cover: /img/training/forensic.png
category: 
  - 'Knowledge'
  - 'Digital Forensics'
---

# Giới thiệu nhanh — Digital Forensics (Điều tra số)

Digital Forensics (Điều tra số) là một nhánh của khoa học điều tra dùng phương pháp, công cụ kỹ thuật và khoa học đã được chứng minh để **thu thập, bảo quản và phân tích dữ liệu trên thiết bị kỹ thuật số**. Mục tiêu là tái hiện sự kiện, xác định hành vi phạm tội hoặc hỗ trợ điều tra các hoạt động trái phép (xâm nhập, tấn công, phá hoại hệ thống, gian lận, gián điệp công nghiệp, v.v.).

---

## Khi nào cần thực hiện một cuộc điều tra số?

* Khi hệ thống bị tấn công mà **chưa xác định được nguyên nhân**.
* Khi cần **khôi phục dữ liệu** đã bị xóa trên thiết bị hoặc hệ thống.
* Khi điều tra tội phạm có liên quan đến công nghệ cao.
* Điều tra **gian lận** trong tổ chức.
* Điều tra các hoạt động **gián điệp công nghiệp**.

---

## Roadmap — Lộ trình học & nghiên cứu

Dưới đây là một lộ trình từ nền tảng đến chuyên sâu để bắt đầu nghiên cứu và thực hành Digital Forensics.

### Kiến thức nền tảng

* **Lập trình**: C/C++, Python, Bash, PowerShell — dùng để viết script phân tích, parse log, hoặc phát triển tools.
* **Hệ điều hành**: Windows, Linux — hiểu cấu trúc file system, registry, service, process.
* **Mạng máy tính**: OSI, TCP/IP, các giao thức (HTTP, DNS, SMTP, v.v.) — để phân tích lưu lượng và incident response.
* **File signature & file format** — nhận diện file, phục hồi dữ liệu.
* **Mã hóa cơ bản**: Base64, ROT, XOR, Hash — thường gặp khi dữ liệu được ẩn/encode.
* **Kiến trúc máy tính** — hiểu memória, disk layout, process model giúp phân tích sâu hơn.

### Kiến thức chuyên sâu

* **Steganography**: ẩn tin trong ảnh, âm thanh, video — phát hiện và trích xuất payload.
* **Artifacts hệ thống**: phân tích log (Windows Event, Linux syslog, Web server logs, Cloud logs).
* **Phân tích lưu lượng mạng**: capture, filter, reconstruct sessions, detect anomalies.
* **Phân tích dữ liệu thiết bị**: RAM forensics, disk forensics, file carving, timeline analysis.
* **SIEM**: thu thập và phân tích dữ liệu từ SIEM (Security Information and Event Management).

---

## Công cụ thường dùng

* **Disk Forensics**: Autopsy, FTK Imager (image, carve, phân tích filesystem).
* **RAM Forensics**: Volatility2, Volatility3 (dump process, tìm inject, phát hiện persistence).
* **Windows Registry**: Regripper (trích xuất artifacts hữu ích từ registry).
* **Network Analysis**: Wireshark, tshark (phân tích pcap, reconstruct TCP/HTTP).
* **Coding / Scripting**: Visual Studio Code (IDE).
* **Distro hỗ trợ**: Kali Linux (chứa nhiều tool phục vụ pentest/forensics).
* **Tiện ích xử lý dữ liệu**: CyberChef (decode, regex, transform nhanh)

---

## Nguồn tài liệu & nền tảng thực hành

Một số trang / nền tảng có labs và challenge để luyện tập Digital Forensics:

* TryHackMe — [https://tryhackme.com](https://tryhackme.com)
* HackTheBox Labs — [https://app.hackthebox.com/](https://app.hackthebox.com/)
* HackTheBox CTF — [https://ctf.hackthebox.com/](https://ctf.hackthebox.com/)
* Let’s Defend — [https://app.letsdefend.io/](https://app.letsdefend.io/)
* CyberDefenders — [https://cyberdefenders.org/](https://cyberdefenders.org/)
* picoCTF — [https://picoctf.org/](https://picoctf.org/)
* Root Me — [https://root-me.org/](https://root-me.org/)
* CTF events trên CTFtime — [https://ctftime.org/](https://ctftime.org/)
* Một số GitHub repo và MemLabs/DFIR labs (tìm theo từ khóa: DFIR, memory forensics, forensic labs)

---

## Gợi ý lộ trình thực hành ngắn hạn

* **Tuần 0–2**: Làm quen môi trường — cài Kali/Windows VM, học Wireshark cơ bản, dùng FTK Imager để tạo image.
* **Tuần 3–6**: RAM forensics với Volatility — phân tích process, network connections, tìmstrings/IOCs.
* **Tuần 7–10**: Disk forensics — recovery file, file carving, timeline.
* **Tiếp theo**: Thực hành trên TryHackMe/HTB labs, tham gia CTF có track Forensics, đọc writeups.

---

## Mẹo & checklist khi thực hiện điều tra số

1. **Bảo toàn chứng cứ**: luôn làm image (bit-by-bit) trước khi phân tích.
2. **Ghi log & chain of custody**: ai đã truy cập, khi nào, thao tác gì.
3. **Xác định mục tiêu phân tích**: timeline, IOC, process suspicious, network artefacts.
4. **Sử dụng sandbox/VM**: phân tích malware / suspicious files trong môi trường cô lập.
5. **Tự động hoá**: viết script để parse log, lọc IOC, trích xuất artifacts nhanh.

---
