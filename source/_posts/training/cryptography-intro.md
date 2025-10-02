---
title: 'Nhập môn mật mã học (Cryptography)'
description: "Nhập môn mật mã học (Cryptography)"
date: 2025-10-02 15:43:03
tags:
  - Knowledge
  - Cryptography
author:
  - armymen
  - d4kw1n
top_img: /img/training/crypto.png
cover: /img/training/crypto.png
category: 
  - 'Knowledge'
  - 'Cryptography'
---

# Giới thiệu nhanh — Chào mừng tới CLB VSL (Cryptography track) 🎉

Chúc mừng bạn đã gia nhập đội **Cryptography**! Mảng crypto trong CTF vừa **rất lý thuyết** lại vừa **rất thực chiến** — bạn sẽ kết hợp toán số, lập trình và tư duy phân tích để “phá” các hệ mã và giải bài toán. Bài viết này tổng hợp **những kiến thức, thuật toán, dạng bài quan trọng, công cụ và lộ trình học** để bạn bắt đầu nhanh và tiến lên được từ cơ bản tới nâng cao.

---

## Những kiến thức nền tảng cần biết

Những thứ này xuất hiện liên tục trong challenge — hãy nắm chắc.

* **Encoding**: base64, hex, ASCII, UTF-8 — biết cách chuyển đổi giữa dạng text và bytes.
* **Hash**: MD5, SHA-1, SHA-256 — hiểu đặc tính (một chiều, va chạm).
* **XOR**: phép toán nền tảng của nhiều hệ mã/cipher và khai thác.
* **Mã hóa đối xứng**: khái niệm khóa chung, ví dụ AES, DES.
* **Mã hóa bất đối xứng**: RSA, ECC — khóa công khai / khóa bí mật.

---

## Toán số & thuật toán cơ bản (bắt buộc)

Crypto nhiều khi chính là “toán ứng dụng” — học kĩ những thứ này:

* **Thuật toán Euclid & Euclid mở rộng** (gcd, tìm inverse mod).
* **Euler totient (φ(n))** — quan trọng với RSA.
* **Fermat nhỏ (Little Fermat)** — dùng trong kiểm tra số nguyên tố, tính lũy thừa mod.
* **Modulo inverse** — nghịch đảo modulo (dùng Euclid mở rộng).
* **Chinese Remainder Theorem (định lý số dư Trung Hoa)** — ghép nghiệm modulo.
* **Quadratic residues / thặng dư bậc hai** — Legendre symbol, kiểm tra có nghiệm căn bậc hai mod p.
* **Tonelli–Shanks** — tìm căn bậc hai modulo p (khi cần).
* **Logarithm rời rạc (Discrete Log)** — vấn đề nền tảng cho nhiều hệ (khó).
* **Coppersmith** — kỹ thuật tấn công RSA (nâng cao).
* **Lattice methods** (LLL, v.v.) — dùng trong tấn công nâng cao (ví dụ: small root problems).

---

## Đại cương về trường và nhóm

(cho bài toán lý thuyết / crypto hiện đại)

* **Galois Field (trường hữu hạn)** — GF(p), GF(2^n) — quan trọng cho AES, ECC.
* **Nhóm trong Galois Field** — phép toán, tính đồng nhất, bậc phần tử.
* **Polynomial rings** — đa thức trên trường, modulus đa thức (dùng trong ECC, coding).
* **Modulo arithmetic** — mọi thứ đều quay quanh mod.

---

## Những dạng mã phổ biến (và nhanh cách nhận diện)

Từ đơn giản tới nâng cao — nhiều bài CTF là biến thể hoặc ghép nhiều dạng:

**Dạng cổ điển / đơn giản**

* Caesar cipher
* Affine cipher
* Auto-key cipher
* Substitution / Vigenère

**Dạng chuẩn / hệ thống**

* **RSA** (chìa khoá công khai, ký số): hiểu keygen, encrypt/decrypt, padding issues.
* **ECC** (Elliptic Curve Cryptography).
* **Diffie–Hellman** (key exchange — đôi khi xuất hiện dưới dạng flawed DH).
* **AES**, **DES** — symmetric block ciphers.

**Cấu thành cipher / block**

* Permutation box, Substitution box (S-box), Round keys — hiểu kiến trúc block cipher.

---

## Thuật toán & kỹ thuật nâng cao (spotlight)

* **Tonelli–Shanks** — căn bậc hai modulo (practical).
* **Coppersmith** — tấn công nghiệm nhỏ trên RSA (nâng cao).
* **Lattice attacks (LLL)** — dùng để phá một số khóa hay bài toán small-solution.
* **Discrete log algorithms** (Baby-step Giant-step, Pollard Rho).

---

## Web luyện tập & bài tập thực hành

* **Cryptohack** — lộ trình từ cơ bản tới nâng cao, nhiều bài có giải thích.
* **PicoCTF** — tập trung vào thực hành, phù hợp người mới bắt đầu.
  (ngoài ra: Root-Me, HackTheBox, CTFtime có các challenge crypto trong các cuộc thi)

---

## Công cụ & thư viện thiết yếu

* **Công cụ trực quan / nhanh**: CyberChef (tiền xử lý, decode, xor thử nhanh).
* **Cracking / hash**: CrackStation (tra cứu), John the Ripper (offline cracking).
* **Lập trình / scripting**: Python — bắt buộc.
* **Thư viện Python**:

  * `pycryptodome` — thao tác cipher cơ bản (AES, DES, RSA helpers).
  * `gmpy2` — số lớn, tính modulo, kiểm thử primality nhanh.
  * `sage` / Sagemath — mạnh cho toán số và lý thuyết số (nâng cao).
  * `pwntools` — tiện cho tương tác network / gửi payload (dùng trong nhiều CTF đa-lĩnh vực).
  * `requests` — tương tác web (khi challenge có server).

---

## Lộ trình học gợi ý (cấp độ — chỉ mang tính tham khảo)

**Tuần 0–2: Chuẩn bị & công cụ**

* Nắm base64/hex/ASCII, chuyển đổi, dùng CyberChef.
* Làm vài bài Caesar / Vigenère / XOR trên PicoCTF.

**Tuần 3–6: Toán số cơ bản + ciphers cổ điển**

* Học Euclid, inverse mod, Euler phi, Fermat.
* Thực hành: các challenge liên quan RSA nhỏ (demo e=3, n nhỏ), breaking Vigenère.

**Tháng 2–3: Asymmetric & symmetric sâu hơn**

* Tìm hiểu RSA chi tiết (keygen, encryption, padding pitfalls).
* AES, DES — block modes (ECB/CBC/CTR) và các lỗi thường gặp.

**Tháng 4 trở đi: Kỹ thuật nâng cao**

* Tonelli–Shanks, discrete log, lattice basics, attacks (Coppersmith).
* Tham gia CTF thật, làm team, đọc editorials (giải thích) sau khi solve.

---

## Mẹo thực chiến & checklist khi gặp bài Crypto

1. **Đọc kỹ đề** — tìm keywords: “base64”, “mod”, “encoded”, “public key”, “prime”, v.v.
2. **Convert to bytes** — trước khi thao tác, đưa input về bytes/hex.
3. **Thử các decode đơn giản**: base64 → hex → ascii; thử ASCII shifts (Caesar).
4. **Kiểm tra XOR**: thử khóa ngắn / key repeat (Vigenère-like).
5. **Với RSA**: kiểm tra gcd(e, φ(n)), small e, small d, repeated primes, common modulus.
6. **Ghi lại mọi giả thuyết** — nhiều challenge ghép nhiều lỗi nhỏ.
7. **Script hoá**: viết script Python để thử nhiều biến thể nhanh.

---

## Mẫu checklist đặt mục tiêu cho tuần đầu

* [ ] Lướt qua Cryptohack: hoàn thành các challenge “Intro”.
* [ ] Viết script nhỏ để base64 ⇄ hex ⇄ ascii tự động.
* [ ] Giải 3 bài Caesar/Affine/Auto-key.
* [ ] Học Euclid & implement inverse_mod trong Python.
* [ ] Cài CyberChef, pycryptodome, gmpy2.

---

## Kết luận & Lời khích lệ

Crypto trong CTF đôi khi có thể **rất toán** nhưng cũng cực kỳ **thú vị** khi bạn nhìn thấy mạch logic lộ ra và “bẻ” được hệ mã. Bắt đầu bằng những bài đơn giản, xây nền tảng toán số và viết nhiều script — rồi dần dần thử các kỹ thuật nâng cao. Tham gia thảo luận trong nhóm, chia sẻ writeup sau mỗi challenge — đó là cách tiến nhanh nhất.
