# tea-trends-uz 🍵

Daily сбор трендов поисковых запросов по сортам китайского чая (Узбекистан, Google Trends).

`generate.py` тянет данные через `pytrends` (cat=71 «Еда и напитки», geo=UZ) и
собирает статичный `index.html` с графиками на Chart.js. Если Google Trends
недоступен — используются fallback-данные, чтобы сайт не падал.

## Как развернуть

1. Создай новый публичный репозиторий на GitHub и залей туда все файлы
   (`generate.py`, `index.html`, `.github/workflows/update.yml`, `README.md`).
2. Settings → Pages → Source → **Deploy from a branch** → `main` / `/ (root)`.
3. Settings → Actions → General → Workflow permissions →
   **Read and write permissions** (иначе автокоммит из workflow не сможет пушить).
4. Готово — сайт появится на `https://<юзер>.github.io/<репозиторий>/`.
   Workflow гоняется раз в сутки (06:35 UTC) и коммитит обновлённый `index.html`.
   Можно запустить и вручную: вкладка **Actions → Update tea trends → Run workflow**.

## Локальный запуск

```bash
pip install pytrends pandas
python generate.py
```

## Что можно поменять

- `BRAND_GROUPS` / `MODEL_GROUPS` в `generate.py` — список категорий и сортов чая
  (сейчас: зелёный, улун, пуэр, хунча, белый, жёлтый — и по 3–5 знаменитых сортов в каждой).
- `GEO` — регион Google Trends (сейчас `UZ`).
- `CATEGORY` — категория Google Trends (сейчас `71`, «Еда и напитки»).
