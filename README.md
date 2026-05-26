# Ring0 - Custom Linux Kernel Module

Repository ini berisi kode sumber untuk modul kernel Linux (LKM) kustom yang beroperasi pada tingkat hak akses tertinggi sistem (**Ring 0**). Modul ini mengimplementasikan teknik interupsi fungsi (*function hooking*) di dalam kernel space untuk keperluan analisis keamanan dan manajemen hak akses terisolasi.

## Fitur Utama

* **Kernel-level Hooking**: Melakukan intersepsi pada fungsi sistem kritis (seperti `kill`, `getuid`).
* **Privilege Escalation Mechanism**: Fungsi internal (`SpawnRoot` / `rootmagic`) untuk memanipulasi kredensial proses secara langsung di memory space kernel.
* **Low-level Stealth**: Berjalan langsung di ruang kernel, memungkinkannya mengontrol perilaku sistem operasi di bawah tingkat *user space*.

---

## Prasyarat & Dependensi

Untuk melakukan kompilasi (*compile*) modul kernel ini, sistem Linux harus memiliki peralatan pengembangan (*development tools*) dan berkas header yang sesuai dengan versi kernel yang sedang berjalan.

### Paket yang Diperlukan:
* **`gcc`**: Kompiler C untuk memproses kode sumber Ring 0.
* **`make`**: Utilitas untuk mengotomatisasi proses pembangunan biner.
* **Linux Kernel Headers**: Diperlukan agar modul dapat berinteraksi dengan struktur data internal kernel.

### Perintah Instalasi Dependensi:

**Pada Rumpun Debian / Ubuntu:**
```bash
sudo apt update
sudo apt install build-essential gcc linux-headers-$(uname -r) -y
