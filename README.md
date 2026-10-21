# Satsangs in Chennai

A single-page static site listing satsangs in Chennai. The page is `index.html`; all listings live in `listings.json`, so you only edit data, never HTML.

## Add or edit a listing

Open `listings.json`. It has two lists:

- `dated`: events with specific dates. Give either
  - `"dates": ["2026-11-05", "2026-11-06"]` (ISO dates, `YYYY-MM-DD`), or
  - `"rule": "firstSunday"` to repeat on the first Sunday of every month.
- `regular`: ongoing gatherings without fixed dates. Use `"when"` to describe the schedule in words.

Fields (only `title` and `who` are required; leave out anything you don't know):

| Field | Used in | Meaning |
|---|---|---|
| `title` | both | Name of the satsang |
| `ta` | dated | Tamil title, shown beside the English one |
| `who` | both | Teacher or organisation |
| `dates` / `rule` | dated | When it happens (see above) |
| `time` | dated | e.g. `"6:30–8:30 PM"` |
| `when` | regular | e.g. `"Weekly, Sundays 6 PM"` |
| `where` | both | Venue |
| `lang` | dated | Language |
| `entry` | both | Cost or who can attend |
| `note` | both | Short extra detail |
| `url`, `urlText` | both | Link and its label |

Example dated entry:

```json
{
  "title": "Bhagavad Gita talks",
  "who": "Swami X",
  "dates": ["2026-11-07", "2026-11-08"],
  "time": "6–7:30 PM",
  "where": "Mylapore",
  "entry": "Free"
}
```

Keep the JSON valid: double quotes, commas between entries, no trailing comma. Check it with `python3 -m json.tool listings.json`.

Also update the "Listings last checked" date in the footer of `index.html` when you refresh the data.

## Preview locally

`fetch` doesn't work from `file://`, so serve the folder:

```sh
python3 -m http.server 8000   # then open http://localhost:8000
```

## Publish

Commit and push to `main`; GitHub Pages redeploys automatically.
