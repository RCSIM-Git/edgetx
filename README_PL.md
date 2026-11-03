# EdgeTX — Oprogramowanie Układowe Aparatur RC (Fork RCSIM z Pełnym Dupleksem CRSF USB-VCP)

[![GitHub release](https://img.shields.io/github/v/release/Edgetx/edgetx)](https://github.com/EdgeTX/edgetx/releases/latest)
[![License: GPL v2](https://img.shields.io/badge/License-GPL_v2-blue.svg)](https://www.gnu.org/licenses/old-licenses/gpl-2.0.html)
[![Discord](https://img.shields.io/discord/839849772864503828.svg?label=&logo=discord&logoColor=ffffff&color=7389D8&labelColor=6A7EC2)](https://discord.gg/wF9wUKnZ6H)

> 🌐 **Language / Język:** [English](README.md) | **Polski**

Witaj w **EdgeTX** — zaawansowanym oprogramowaniu open-source dla aparatur i nadajników RC!

Niniejsze repozytorium stanowi **deweloperski fork RCSIM** systemu EdgeTX. Łączy ono główną gałąź EdgeTX z PR **#7630** (*CRSF Trainer over USB-VCP*) oraz autorskim **silnikiem klonowania telemetrii w pełnym dupleksie (	elemetrySetMirrorCb)**. Pozwala to aparaturom RC (m.in. RadioMaster MT12, Pocket, Boxer, TX16S, TX12 i Zorro) pracować jako dwukierunkowe transceivery CRSF o niskim opóźnieniu za pośrednictwem jednego kabla USB-C.

---

## 🚀 Kluczowe Usprawnienia RCSIM: Pełny Dupleks CRSF USB-VCP

Modyfikacje (dostępne na gałęzi pr/full-duplex-telemetry-mirror) zapewniają:
* 🏎️ **Sterowanie Wejściowe (PC $\rightarrow$ Radio):** Przesyłanie 16 kanałów RC (100–250 Hz) ze stacji naziemnej PC (RCSIM-GCS, kierownica sim-racingowa, pedały, wolant) bezpośrednio do miksera EdgeTX i nadajnika ELRS.
* 🛰️ **Telemetria Zwrotna (Radio $\rightarrow$ PC):** Klonowanie pakietów telemetrii z modelu w czasie rzeczywistym (napięcie akumulatora, Link Statistics / RSSI / LQ / SNR, współrzędne GPS, orientacja IMU) przez wirtualny port COM (USB-VCP) z powrotem do komputera dla układu Force Feedback (FFB) i wskaźników kokpitu.
* 🔌 **Zero Dodatkowych Adapterów:** Bezpośrednie połączenie standardowym kablem USB-C — brak konieczności stosowania zewnętrznych płytek FTDI, kabli trenera czy dodatkowych odbiorników na biurku.

### Obsługiwane Aparatury i Optymalizacja Pamięci
- **RadioMaster MT12:** Aparatura pistoletowa/kołowa do aut i łodzi RC.
- **RadioMaster Pocket:** Wersja zoptymalizowana pod 512KB pamięci Flash STM32 (usunięto przestarzałe protokoły PXX/Heli).
- **RadioMaster Boxer, TX16S/MKII, TX12/MKII, Zorro:** Wersje przetestowane i zweryfikowane na stanowisku pomiarowym.

---

## 🛠️ Kompilacja Oprogramowania ze Źródeł

### Wymagania
* CMake 3.20+
* Zestaw narzędzi rm-none-eabi-gcc 10.3+
* Python 3.8+ z bibliotekami jinja2 oraz pillow

### Przykład Budowania (RadioMaster MT12):
`ash
git checkout pr/full-duplex-telemetry-mirror
mkdir -p build && cd build
cmake -DPCB=MT12 -DPCBREV=REV00 -DCMAKE_BUILD_TYPE=Release ..
make -j$(nproc)
`

Skompilowany plik binarny (mt12-*.bin) wgrywa się za pomocą **EdgeTX Bootloadera** (przytrzymanie poziomych trymerów do wewnątrz podczas włączania zasilania).

---

## 📖 O Projekcie Bazowym EdgeTX

EdgeTX to wiodący projekt społeczności modelarskiej rozwijający oprogramowanie OpenTX:
* **Społeczność:** [EdgeTX Discord](https://discord.gg/wF9wUKnZ6H) | [Dyskusje GitHub](https://github.com/EdgeTX/edgetx/discussions)
* **Oficjalny Podręcznik:** [Instrukcja Użytkownika EdgeTX](https://manual.edgetx.org/)
* **Dokumentacja Lua:** [Baza Wiedzy Lua EdgeTX](https://luadoc.edgetx.org/)

---

## 📜 Licencja

Oprogramowanie dystrybuowane na licencji [GNU General Public License v2.0 (GPL-2.0)](https://www.gnu.org/licenses/old-licenses/gpl-2.0.html).
