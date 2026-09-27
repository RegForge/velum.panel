# Render deploy

Three files, drop them at the ROOT of a private GitHub repo:

- app.py            (self-contained panel + frontend)
- requirements.txt
- render.yaml       (Render Blueprint)

Then on Render:

1. New -> Blueprint -> pick the repo. It creates the web service from render.yaml.
2. Service -> Environment -> set:
   - DATABASE_URL = your Neon postgres URL (sslmode=require)
   - PLISIO_API_KEY = your Plisio key
   - PANEL_ADMIN_TOKEN = your admin password (leave unset = auto-generated, printed in logs)
3. Deploy. Render gives you https://<service>.onrender.com.
4. Plisio dashboard -> settings -> allowed domains -> add that onrender.com URL.
5. Open the panel on that URL, claim it, open sign-ups, test the buy.

Free tier: sleeps after ~15 min idle, cold start ~1 min. State lives in Postgres (Neon), never on disk.
