# MarvelWarfront

## Leaderboard integration

The leaderboard UI is ready for a game-data API, but this site does not include Roblox Studio scripts or a backend. The Roblox scripter can connect the game stats using their preferred server-side setup.

Set the `leaderboard-api` meta tag in `index.html` to the API URL, for example `/api/leaderboard` for a same-origin endpoint. The page requests that URL with `stat=kills`, `stat=wins`, or `stat=deaths`, plus `limit=25`.

Expected JSON response:

```json
{
	"updatedAt": "2026-09-30T12:00:00.000Z",
	"entries": [
		{ "userId": 123456, "username": "PlayerName", "displayName": "Player", "value": 42 }
	]
}
```

The API must return entries sorted from highest to lowest `value`. Keep Roblox credentials on the server; never put an Open Cloud key in this page or a LocalScript. If the API is on a different domain, it must allow requests from this site's origin.

