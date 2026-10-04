# Hold (OfficeHours)

Campus office-hours board. TAs post twenty-minute slots. Students hold one, read any private note the TA left, cancel, or pass the slot to a classmate.

Flask, Jinja, SQLite.

## Run locally

```
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
python app.py
```

Open http://localhost:3000. The database is created and seeded on first request.

## Demo accounts

- lea@campus.edu / campus123 — student (holds two slots)
- nico@campus.edu / campus123 — student
- ravi@campus.edu / ta-office — TA

## Security fix

Case Study 3 patch: the device-handoff link used to carry the raw session token in the URL (`/me?sid=<token>`), so anyone who got the link was logged in as that student. Replaced it with a single-use, 15-minute handoff code that mints a fresh session and is consumed on first use; the session is now read only from the cookie. See `SECURITY_WRITEUP.md`.
