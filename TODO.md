# Backend Fix and Run Plan

- [x] Edit backend/app/models.py: Add `from typing import Optional`; replace `Mapped[str | None]` with `Mapped[Optional[str]]` for emails.
- [ ] Run new server command: `cmd /c "cd backend & call venv\\Scripts\\activate.bat & uvicorn app.main:app --reload --host 0.0.0.0 --port 8000"`
- [ ] Verify /health and /docs accessible.
- [ ] [Optional] Setup .env DATABASE_URL.
