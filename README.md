# allegro-market-engine-info
  Informacje o aplikacji AllegroMarketEngine — lokalnym narzędziu do analizy opłacalności własnych ofert Allegro.
# Allegro Market Engine

Lokalny system analityczny wspierający ręczną sprzedaż kluczy do gier na Allegro.
Tylko odczyt i rekomendacje — **nie publikuje i nie edytuje żadnych ofert**.

Pełny opis zakresu i reguł: [SPECIFICATION.md](SPECIFICATION.md).

Wszystkie polecenia zakładają **Git Bash**.

> Na Windowsie `python` w PATH bywa zaślepką Microsoft Store, która kończy się błędem.
> Wtedy zamiast `python` użyj `py -3.12`. Projekt wymaga Pythona 3.12 lub nowszego.

## Uruchomienie

    cp .env.example .env           # uzupełnij hasła i sekrety
    docker compose up -d
    python -m venv .venv
    .venv/Scripts/pip install -e ".[dev]"
    .venv/Scripts/alembic upgrade head
    .venv/Scripts/uvicorn app.main:app --host 127.0.0.1 --port 8000

Panel: http://127.0.0.1:8000

## Odtworzenie dokładnych wersji zależności

    .venv/Scripts/pip install -r requirements.lock && .venv/Scripts/pip install -e . --no-deps

## Kontrola jakości

    .venv/Scripts/pytest
    .venv/Scripts/ruff check .
    .venv/Scripts/mypy app

Testy jednostkowe działają bez bazy i bez `.env`:

    .venv/Scripts/pytest tests/unit
