# UBYS — Üniversite Bilgi Yönetim Sistemi

Kastamonu Üniversitesi öğrenci bilgi sistemi. Frontend ve backend ayrı repolar olarak yönetilmekte olup bu repo ikisini birden içermektedir.

## Gereksinimler

| Araç | Minimum Sürüm |
|------|--------------|
| Git | 2.13+ |
| Node.js | 20+ |
| Docker & Docker Compose | 24+ |

## Kurulum

### 1. Repoyu klonla

```bash
git clone --recurse-submodules https://github.com/UBYS-Lab/main ubys
cd ubys
```

> Eğer `--recurse-submodules` yazmadan klonladıysan:
> ```bash
> git submodule update --init --recursive
> ```

### 2. Tüm servisleri başlat

```bash
docker compose up --build -d
```

| Servis | URL |
|--------|-----|
| Frontend | http://localhost:4000 |
| Backend API | http://localhost:8001 |

## Repo Yapısı

```
ubys/
├── ubys-frontend/   → Angular uygulaması  (github.com/UBYS-Lab/frontend)
└── ubys-backend/    → Laravel API         (github.com/UBYS-Lab/backend)
```

## Alt Repolarda Değişiklik Yapmak

Değişiklikler doğrudan `ubys-frontend/` veya `ubys-backend/` klasörlerinde ilgili repoya push edilir:

```bash
cd ubys-frontend   # veya ubys-backend
git checkout -b feature/yeni-ozellik
# ... değişiklikler ...
git add -A
git commit -m "feat: açıklama"
git push origin feature/yeni-ozellik
```

Ardından GitHub'da ilgili repo üzerinden pull request açılır. CI pipeline otomatik olarak build ve testleri çalıştırır.
