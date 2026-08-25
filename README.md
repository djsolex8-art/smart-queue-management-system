# Smart Queue Management System (SQMS)

A web-based queue management system for university student service centres.

## Quick Start (Local)

```bash
pip install -r requirements.txt
python app.py
```
Visit http://127.0.0.1:5000

**Demo credentials:**
- Admin: `admin` / `Admin@123`
- Staff: `staff01` / `Staff@123`
- Students: register at `/register`

## Deploy to Render.com

1. Push this repo to GitHub
2. Go to render.com → New → Web Service
3. Connect your GitHub repo
4. Set these environment variables:
   - `DATA_DIR` = `/opt/render/project/src/data`
   - `SECRET_KEY` = (generate a random string)
5. Add a Disk: mount path `/opt/render/project/src/data`, size 1GB
6. Deploy

## Tech Stack
- Python 3.12 + Flask 3.1
- SQLite (persistent disk on Render)
- Gunicorn (production server)


## Vercel + Supabase deployment

This project can run on Vercel using the Flask WSGI entry point at `api/index.py`.
Set `DATABASE_URL` in Vercel to the Supabase **Transaction Pooler** connection string (port 6543), which Supabase recommends for serverless functions. Set `SECRET_KEY` to a strong random value.

The existing Render `Procfile` and `render.yaml` are retained so the Render deployment can be used as a rollback option.
