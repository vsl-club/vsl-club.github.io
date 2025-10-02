---
title: 'Nhập môn Khai thác nhị phân (Binary Exploitation - PWN)'
description: "Nhập môn Khai thác nhị phân (Binary Exploitation - PWN"
date: 2025-10-02 15:43:03
tags:
  - Knowledge
  - PWN
author:
  - armymen
  - d4kw1n
top_img: /img/training/pwn.png
cover: /img/training/pwn.png
category: 
  - 'Knowledge'
  - 'PWN'
---

# Giới thiệu nhanh — Binary Exploitation (PWN)

Binary Exploitation (thường gọi tắt là **PWN**) là mảng rất thực chiến trong CTF: bạn làm việc trực tiếp với mã máy, định dạng tệp thực thi (ELF/PE), nhớ, và tương tác với chương trình để tìm lỗ hổng và khai thác chúng nhằm chạy mã tuỳ ý hoặc leo privilege. Bài viết này tóm tắt kiến thức cần nắm, kỹ thuật tấn công phổ biến, công cụ thiết yếu, lộ trình học và mẹo thực chiến.

---

## Kiến thức nền tảng

* **Hệ điều hành & kiến trúc**: Linux (đặc biệt), Windows (không bắt buộc lúc đầu), kiến trúc x86/x86_64, calling convention (cdecl, syscall).
* **Assembly**: đọc/hiểu ASM cơ bản (mov, call, ret, push/pop, lea, xor, jne,...).
* **Định dạng thực thi**: ELF (headers, sections, .text/.data/.bss), libc, dynamic linking.
* **C/low-level programming**: con trỏ, stack, heap, buffer, format strings.
* **Mô hình bộ nhớ**: stack layout, heap chunks, memory mappings.

---

## Lỗ hổng & kỹ thuật cơ bản (must-know)

* **Buffer overflow (stack)** — overwrite return address, ret2libc, ROP.
* **Stack canaries** — phát hiện & bypass (info leak, ret2win trong số ít trường hợp).
* **NX/DEP** — không cho chạy vùng dữ liệu; dùng ROP để vượt.
* **ASLR** — Address Space Layout Randomization; cần leak address để bypass.
* **PIE** — Position Independent Executable, binary base randomized.
* **Format string** — leak memory, write arbitrary memory.
* **Heap exploitation**: fastbin, tcache, unsorted-bin, use-after-free, double-free, House of Force/House of Spirit, heap leak → arbitrary write/execute.
* **Integer overflow / underflow** — gây buffer size miscalc.
* **Race conditions / TOCTOU** — nâng cao, thường trong pwn/challenges hệ thống.

---

## Kỹ thuật & công cụ tấn công nâng cao

* **Return-to-libc (ret2libc)** — gọi system("/bin/sh") bằng địa chỉ libc.
* **Return Oriented Programming (ROP)** — xâu các gadgets (ret; pop rdi; ret;...) để điều khiển luồng thực thi.
* **ROP chain builders**: ROPgadget, Ropper, rp++ (trong pwntools).
* **Format string exploitation**: leak & write bằng %n.
* **Heap techniques**: tcache poisoning, fastbin dup, unsortedbin leak → libc leak → hijack __malloc_hook / free hook / vtable.
* **Bypassing mitigations**: combine info leak + ROP + ret2libc + heap primitives.

---

## Công cụ thiết yếu

* **GDB + GEF / peda / pwndbg** — debug, set breakpoints, inspect memory/registers, tìm gadgets.
* **Pwntools (Python)** — automation exploit, tương tác process/remote, packing/unpacking.
* **objdump / readelf / nm / strings / ldd** — inspect binary, symbol tables, dependencies.
* **checksec** — kiểm tra NX, PIE, Canary, RELRO.
* **ROPgadget / Ropper / radare2 / Cutter** — tìm gadgets, phân tích binary.
* **strace / ltrace** — theo dõi system calls / library calls.
* **seccomp tools** nếu challenge có sandbox/filters.
* **Static analysis**: IDA Pro, Ghidra (decompiler) — đọc nhanh logic chương trình.

---

## Nền tảng luyện tập (web & CTF)

* **pwnable.kr** — bài pwn cơ bản → nâng cao.
* **pwnable.tw** — collection nhiều bài thú vị.
* **ROP Emporium** — tập trung vào ROP (từ dễ đến khó).
* **HackTheBox (PWN labs & challenges)** — real-world style.
* **TryHackMe (PWN rooms)** — guided labs.
* **CTFtime** — tham gia các CTF có track pwn.
* **Google CTF / DEF CON Quals / PlaidCTF writeups** — đọc writeups để học patterns.

---

## Lộ trình học gợi ý (cấp độ)

**Tuần 0–2: Chuẩn bị & công cụ**

* Cài môi trường: VM Linux, GDB + GEF, pwntools, radare2/Ghidra.
* Làm vài bài buffer overflow đơn giản (pwnable.kr / ROP Emporium easy).

**Tuần 3–6: Stack & ROP**

* Ôn lại assembly, stack frame, return address overwrite.
* Học ret2libc, ROP chain, tìm gadgets, bypass NX.
* Practice: ROP Emporium, pwnable.tw challenges.

**Tuần 7–12: Heap exploitation**

* Hiểu malloc/free, chunk metadata, tcache/fastbin/unsorted bin.
* Thực hành tcache poisoning, fastbin dup, leak libc từ unsorted bin.
* Làm các bài heap trên pwnable.tw, some HTB boxes.

**Tháng 4 trở đi: Kỹ thuật nâng cao**

* ROP chain phức tạp, fullchain exploit (info leak → leak libc → ROP).
* Bypass mitigations (PIE, Canary, RELRO).
* Kernel pwn / exploit chaining nếu bạn muốn chuyên sâu.

---

## Mẹo thực chiến & checklist khi gặp bài PWN

1. **Chạy binary local**: chạy với arguments, thử input, xem crash.
2. **Checksec**: xác định mitigations (NX, PIE, Canary, RELRO).
3. **Tìm vuln nhanh**: buffer overflow? format string? heap bug? đọc source nếu có.
4. **Leak thông tin**: tìm ways để leak stack/libc addresses (puts, printf, format, heap leak).
5. **Xây payload**: dùng pwntools để pack addresses, xây ROP chain.
6. **Debug**: chạy dưới GDB để check offsets, gadgets, payload length.
7. **Automate & harden**: viết script có thể tương tác remote (remote host/port).

---

## Checklist cho tuần đầu (gợi ý)

* [ ] Cài GDB + GEF/pwndbg, pwntools, ROPgadget.
* [ ] Làm 5 bài buffer overflow đơn giản.
* [ ] Viết exploit template pwntools (connect local/remote, send/recv, pack/unpack).
* [ ] Học dùng objdump/readelf/strings để thu thập info nhanh.

---

## Tài nguyên học thêm & đọc writeups

* Writeups trên GitHub của các team CTF (ví dụ: 0xdf, dragon sector, night-shift).
* ROP Emporium writeups và giải thích.
* Các bài blog về heap exploitation (tcache, fastbin) và giải thích chi tiết.

---
