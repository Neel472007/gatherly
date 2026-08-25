# Gatherly

A runnable browser MVP for a temporary group meetup map.

## Run it

From this folder, start a local server:

```powershell
npm start
```

Then visit [http://localhost:5173](http://localhost:5173). A local server is required for the browser to offer live location permission.

## Deploy safely

Railway or Render can run this Node server using the existing `npm start` command. Set no fixed port: the app reads the platform-provided `PORT` variable automatically. Enable a persistent disk if you want the temporary local account-file storage to survive service restarts.

The repository includes `railway.toml` and `render.yaml`, so either host detects the start command automatically after importing the GitHub repository.

For a real public release, replace `.gatherly-users.json` and in-memory journeys with Supabase/Postgres before inviting users. A public deployment also needs HTTPS for live location on phones.

## What works

- Create a named meetup and an invite code.
- See four friends, a shared destination, straight-line distance, and a calculated ETA.
- Enable your browser's live geolocation (including live updates as you move).
- Change a destination, including by clicking directly on the map.
- Move the demo friends, copy/share an invite, and end the meetup.
- Share a member link; members who join through it see the shared group state through the local realtime server.

## Important MVP limitation

This is a local MVP: journeys are retained only while the server is running. Account records are persisted to a local, git-ignored file so sign-in survives a restart in local development. To deploy publicly, use a managed database such as Supabase/Postgres for accounts and journeys; do not rely on the local account file in a serverless or multi-instance deployment. Deploy behind HTTPS because mobile geolocation requires a secure origin.
