---
title: 'Nhập môn Dịch ngược (Reverse Engineering)'
description: "Nhập môn Dịch ngược (Reverse Engineering)"
date: 2025-10-02 15:43:03
tags:
  - Knowledge
  - Reverse
author:
  - armymen
  - d4kw1n
top_img: /img/training/re.png
cover: /img/training/re.png
category: 
  - 'Knowledge'
  - 'Reverse'
---

# Giới thiệu nhanh — Reverse Engineering (RE)

Reverse Engineering (RE) — hay phân tích ngược — là mảng tập trung vào **hiểu cấu trúc và hành vi của chương trình** khi không có (hoặc có ít) source code. Trong CTF, RE thường xuất hiện dưới dạng: crackme, reversing challenge, unpacking binary, hoặc phân tích malware. Mục tiêu: đọc được logic chương trình, tìm khóa/flag, hoặc xác định điểm yếu để khai thác.

---

## Những kiến thức nền tảng

* **Assembly & kiến trúc**: x86/x86_64, ARM (nhất là nếu có firmware/IoT), calling conventions.
* **Ngôn ngữ bậc cao**: hiểu C/C++ giúp hiểu cấu trúc mã khi đọc ASM.
* **Định dạng thực thi**: ELF (Linux), PE (Windows), Mach-O (macOS) — headers, imports, sections.
* **Chuỗi thực thi & flow**: function boundaries, control flow graph (CFG), stack/heap usage.
* **Encoding/Obfuscation**: base64, custom encodings, XOR, simple packing.

---

## Kỹ thuật phân tích (static & dynamic)

* **Static analysis**: đọc ASM, dùng decompiler (Ghidra/IDA) để hiểu cấu trúc hàm, tìm strings, cross-references.
* **Dynamic analysis**: debug bằng GDB/WinDbg/x64dbg, chạy sample trong sandbox, theo dõi runtime behavior.
* **Hybrid analysis**: kết hợp static + dynamic (ví dụ: dùng decompiler để định vị hàm, debug để xem biến runtime).
* **Symbolic execution & concolic testing**: angr, Triton — tự động hoá tìm input thoả điều kiện (tìm flag bypass checks).
* **Binary diffing / patching**: find differences between versions (BinDiff, Diaphora), patch binary để bypass checks.

---

## Các dạng challenge & patterns hay gặp

* **Crackme**: tìm license key hoặc bypass check.
* **Obfuscated / packed binary**: UPX, custom packers — phải unpack để phân tích.
* **License / serial checks**: tìm thuật toán check và tạo key.
* **Anti-debug / anti-tamper**: kỹ thuật phát hiện debugger, self-modifying code — cần bypass.
* **Protocol / firmware reversing**: phân tích giao thức hay firmware cho thiết bị IoT.

---

## Công cụ thiết yếu

* **Decompilers / Disassemblers**: Ghidra (miễn phí, mạnh), IDA Pro (cao cấp), radare2/Cutter.
* **Debugger**: GDB (Linux), x64dbg / OllyDbg / WinDbg (Windows).
* **Binary utilities**: objdump, readelf, strings, nm, ldd.
* **Patching**: rizin/cutter, Hiew, python + pwntools để patch bytes.
* **Symbolic execution / analysis**: angr, Triton.
* **Dynamic instrumentation**: frida, PIN, DynamoRIO — hook API, taint, trace.
* **Unpackers / packer tools**: UPX, generic unpacking scripts.
* **Firmware tools**: binwalk, firmware-mod-kit, qemu for emulation.

---

## Kỹ năng hữu ích khác

* **Regex & scripting**: Python để tự động hoá việc tìm pattern, extract strings, build fuzzer.
* **Fuzzing**: afl, honggfuzz — tìm inputs gây crash, phát hiện điều kiện logic.
* **Reverse network protocols**: tcpdump/wireshark + scapy để tái tạo/khảo sát giao thức.
* **Format understanding**: file headers, serialization formats (protobuf, ASN.1).

---

## Lộ trình học gợi ý

**Tuần 0–2: Nền tảng & công cụ**

* Cài Ghidra / radare2 / x64dbg, làm quen GUI/shortcuts.
* Học assembly cơ bản (x86/x86_64) và cách map từ C sang ASM.

**Tuần 3–6: Static reversing & decompiler**

* Thực hành read-only: tìm strings, cross references, reconstruct logic bằng decompiler.
* Giải vài crackme đơn giản (keygenme, serial check).

**Tuần 7–12: Dynamic reversing & anti-debug**

* Debugging: đặt breakpoint, xem registers, theo dõi stack/heap.
* Bypass các cơ chế anti-debug đơn giản (sleep, ptrace, isDebuggerPresent).

**Tháng 4 trở đi: Tự động hoá & symbolic execution**

* Học angr / Triton để tự động tìm input thoả điều kiện.
* Reverse firmware / protocol nếu muốn làm IoT/embedded.

---

## Nền tảng luyện tập & resources

* **Crackmes.one** — kho crackme các mức độ.
* **reversing.kr** — bài reversing truyền thống.
* **Manticore / angr challenges** — symbolic execution practice.
* **Flare-On** — CTF/reverse oriented.
* **CTFtime** — tham gia giải bài reversing trong các CTF.
* **Writeups & blogs**: sử dụng writeups của các team để học patterns.

---

## Mẹo thực chiến & checklist khi bắt đầu 1 bài RE

1. **Thu thập thông tin**: strings, checksums, packer (UPX?), imports (API list).
2. **Xác định entry points**: hàm main / init / handler.
3. **Tìm nhanh checks**: locate compare operations, strcmp,memcmp, lstrcmp.
4. **Nếu packed**: unpack (UPX -d) hoặc run in debugger & dump unpacked memory region.
5. **Debug run-through**: set breakpoint trước check, observe inputs/registers.
6. **Tự động hoá**: nếu nhiều branches → consider symbolic execution (angr) để tìm path to success.

---

## Checklist cho tuần đầu

* [ ] Cài Ghidra / x64dbg / radare2.
* [ ] Hoàn thành 5 crackme cơ bản.
* [ ] Viết script Python để extract strings + tìm function references.
* [ ] Thực hành unpacking UPX binary.

---
