# SCH campus app with unified API backend

This package serves the campus page and the existing API backend from one Render web service. The page calls the server's `/weather` and `/air` routes on the same public address. Other API routes from the source project are not mounted here.

The server uses an in-memory five-minute cache for successful weather and air responses, so opening the page repeatedly does not call the government APIs every time. The API keys remain server-side.

## Deploy on Render

1. Put this project in a GitHub repository you control.
2. In Render, create a **Web Service** connected to that repository.
3. Set the build command to `npm install` and the start command to `npm start`.
4. In the Render service's Environment settings, add the API key values from your private `.env` file:
   - `KMA_SERVICE_KEY`
   - `AIR_SERVICE_KEY`
5. The campus defaults are already set for Asan. Optional overrides are `KMA_NX=60`, `KMA_NY=110`, and `AIR_STATION_NAME=아산`.
6. After the service deploys, open its Render URL. That URL serves the app and its data.

Do not upload `.env` or put API keys in the HTML. Render supplies `PORT` automatically; the server listens on it.

The SQLite request log is local to the service and may reset if the service restarts. It is only for analytics and is not needed for the app's data.
