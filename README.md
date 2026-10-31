# Anime Language API — Search Fix

This API supports partial, case-insensitive title search. The `language` parameter is optional for search. Episodes have only `episodeNumber` and `streamingUrl`; the anime entry still has its main `title`.

## Run in Termux
1. Extract this ZIP.
2. Open Termux and run `termux-setup-storage` if needed.
3. `cd` into the extracted folder (the exact path depends on where you extracted it).
4. Run `npm install`.
5. Run `node --check anime.js` and `node --check server.js`.
6. Run `npm start`.
7. Open `http://127.0.0.1:3000/` in your phone browser while Termux is running.

If `npm` is missing, run `pkg update && pkg install nodejs`.

## Test search
- All entries: `http://127.0.0.1:3000/api/anime`
- Search partial title: `http://127.0.0.1:3000/api/anime/search?title=nar`
- Search without case sensitivity: `http://127.0.0.1:3000/api/anime/search?title=NAR`
- Optional language filter: `http://127.0.0.1:3000/api/anime/search?title=nar&language=English%20Dub`
- All language versions: `http://127.0.0.1:3000/api/anime/title/Re%3AZero`
- Languages present in data: `http://127.0.0.1:3000/api/languages`

## Important
Search can only return anime entries that exist in `anime.js`. Add each anime/language version to that file. Sample poster and streaming URLs using `example.com` are placeholders and must be replaced with valid URLs you are authorized to use.

This ZIP fixes the API backend. If the search bar on your website still fails, its frontend JavaScript must call the API endpoint and render `response.data`. The API ZIP does not contain your website's HTML/CSS/JS files, so share your website search JavaScript (and relevant HTML) to patch the frontend accurately.
