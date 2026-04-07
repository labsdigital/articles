# README.md — Panduan Penggunaan Agen Penulis Artikel

## Apa Ini?

Ini adalah sistem prompt dan panduan untuk membangun agen AI yang menghasilkan artikel analitik-naratif berkualitas tinggi. Dirancang untuk topik teknologi (AI), pendidikan, dan sosial-kemasyarakatan.

---

## Struktur File

```
📁 agent-penulis-artikel/
│
├── CLAUDE.md              ← Profil & identitas agen (sistem prompt utama)
├── SKILL.md               ← Panduan proses menulis artikel langkah demi langkah
├── ARGUMENT_PATTERNS.md   ← Template pola argumen dan logika
├── EXAMPLE_ARTICLE.md     ← Contoh artikel sebagai referensi kualitas
└── README.md              ← Dokumen ini
```

---

## Cara Menggunakan

### Opsi 1: Via Claude.ai Project
1. Buat Project baru di Claude.ai
2. Masukkan isi **CLAUDE.md** sebagai *Custom Instructions* atau *System Prompt* project
3. Upload **SKILL.md**, **ARGUMENT_PATTERNS.md**, dan **EXAMPLE_ARTICLE.md** sebagai Knowledge files
4. Mulai percakapan dan minta artikel

### Opsi 2: Via API
```python
import anthropic

with open("CLAUDE.md", "r") as f:
    system_prompt = f.read()

with open("SKILL.md", "r") as f:
    skill = f.read()

client = anthropic.Anthropic()

message = client.messages.create(
    model="claude-opus-4-5",
    max_tokens=4096,
    system=system_prompt,
    messages=[
        {
            "role": "user",
            "content": f"""Gunakan panduan berikut saat menulis:

<skill>
{skill}
</skill>

Tugas: Tulis artikel tentang [TOPIK ANDA DI SINI]"""
        }
    ]
)
```

### Opsi 3: Prompt Langsung
Salin isi CLAUDE.md sebagai system prompt, lalu mulai dengan:
> "Tulis artikel tentang [topik] untuk pembaca [target audience]. Angle yang ingin saya eksplorasi: [angle spesifik]."

---

## Contoh Permintaan yang Efektif

### ✅ Permintaan yang Spesifik (Lebih Baik)
```
"Tulis artikel tentang dampak AI generatif terhadap pasar kerja kreatif di Indonesia, 
khususnya desainer grafis dan copywriter. Angle: bukan apakah mereka akan digantikan, 
tapi bagaimana definisi 'nilai' pekerjaan kreatif sedang bergeser. 
Target pembaca: profesional muda 25-35 tahun. Panjang: 1.200-1.500 kata."
```

### ⚠️ Permintaan yang Terlalu Luas (Kurang Efektif)
```
"Tulis tentang AI dan pendidikan"
```

---

## Parameter yang Bisa Dikustomisasi

Saat meminta artikel, Anda bisa menentukan:

| Parameter | Contoh |
|-----------|--------|
| **Topik** | AI di sektor kesehatan Indonesia |
| **Angle/Tesis** | Masalah bukan teknologinya, tapi ekosistem datanya |
| **Target Pembaca** | Pejabat kebijakan / mahasiswa / masyarakat umum |
| **Nada** | Lebih akademis / lebih populer / lebih kritis |
| **Panjang** | Brief (600-900 kata) / Standar (1.000-1.500) / Long-form (2.000+) |
| **Format** | Esai naratif / Artikel berita / Opini / Analisis kebijakan |

---

## Tips untuk Hasil Terbaik

1. **Berikan konteks lokal** — sebutkan jika ada kasus atau data Indonesia yang ingin dimasukkan
2. **Tentukan pembaca** — artikel untuk akademisi vs. masyarakat umum sangat berbeda nadanya
3. **Minta kerangka dulu** — untuk artikel panjang, minta outline sebelum full draft
4. **Iterasi adalah normal** — draft pertama untuk didiskusikan, bukan untuk langsung dipublikasikan
5. **Tanya balik** — agen ini akan bertanya klarifikasi jika topik terlalu ambigu; itu tanda sistem bekerja dengan baik

---

## Topik yang Paling Cocok untuk Agen Ini

### Teknologi & AI
- Dampak sosial-ekonomi AI generatif
- Etika pengembangan dan deployment AI
- Kebijakan regulasi AI di Indonesia vs. global
- AI dan kesenjangan digital
- Masa depan pekerjaan di era otomasi

### Pendidikan
- Relevansi kurikulum di era AI
- Literasi digital vs. literasi kritis
- Akses pendidikan dan kesenjangan
- Peran guru di era teknologi
- Pendidikan vokasional dan pergeseran kebutuhan industri

### Sosial-Kemasyarakatan
- Polarisasi digital dan ekosistem informasi
- Dampak media sosial pada kesehatan mental
- Komunitas online dan modal sosial
- Transformasi budaya akibat digitalisasi
- Isu privasi dan surveilans digital

---

*Dikembangkan untuk menghasilkan konten yang analitik, berbasis fakta, dan tetap mengalir sebagai narasi yang menarik.*
