# Assets needed for the case study page

The case study lives at `case-study.html` (served as `/dexforge/case-study`) and is exported to
`Sebastian_Quiroga_StreamDex_CaseStudy.pdf`. Every item below has a visible placeholder frame on the page,
labelled with the same code (A1, A2.1 and so on). Supply the asset, drop it where the row says, and remove the frame.

| Code | What to supply | Where it goes on the page | Notes |
|---|---|---|---|
| A1 | A 60 to 90 second screen recording: a wild Pokémon appears, chat throws balls, someone evolves live with sound, a trade goes through, the Pokédex page opens. Captions, no narration. | Section 0 (header), the 16:9 frame under the links. Replace the `#ph-video` frame with a `<video>` tag or an embedded YouTube/Twitch clip. | An OBS replay or a VOD cut is fine. Keep a copy as MP4 for the application forms that ask for a file. |
| A2.1 | Screenshot: the wild spawn overlay with chat throwing balls. | Section 2, "The game as players see it", frame 1. | Put the files in `assets/case-study/` (create the folder) as `01-spawn.png` and so on, and swap each `.ph` frame for an `<img>`. 1600 px wide or better. |
| A2.2 | Screenshot: the evolution animation on stream. | Section 2, frame 2. | |
| A2.3 | Screenshot: a Buddy sprite next to a chat name. | Section 2, frame 3. | |
| A2.4 | Screenshot: a player's Pokédex page, Summary tab. | Section 2, frame 4. | `pokedex?user=scromf9001` works as a subject. |
| A2.5 | Screenshot: the Pokémart price list (chat or the Shop tab). | Section 2, frame 5. | |
| A2.6 | Screenshot: the Trainer's Handbook page. | Section 2, frame 6. | |
| A3 | Version dates and change lists: the original launch date (March 2025 is a recollection, not confirmed), what V1, V2 and V3 each added and why. | Section 3, "Version history" (`#ph-versions`). Replace the "to confirm" lines and remove the yellow badge. Also fix the launch month badge in section 0 if March 2025 is wrong. | The page already states what the repository history proves: Pokédex site first commit 7 Feb 2026, landing page 19 Feb 2026, Shop tab and Handbook 17 Oct 2026. |
| A4 | Three to five viewer or moderator quotes about the game, each with permission to use the handle. | Section 4, "What players say" (`#ph-quotes`). One `<blockquote>` per quote with the handle as `<cite>`. | Keep them short and specific. Remove the "quotes pending" badge. |
| A5 | The Twitch Channel Analytics export: Creator Dashboard, Analytics, Channel Analytics, date range 1 Sept 2024 to today, Export CSV. Broadcaster login only. | Fill the monthly values into `data/case-study-metrics.json` (average viewers, chat messages, unique chatters per month, Sept 2024 to Sept 2025) and set `exported_on`. The page renders the three charts and the table view on its own; remove the "data pending" badge in section 4 once the numbers are in. | Leave a value `null` if a month is unknown. A metric needs at least two months with numbers to draw. If the file is empty or missing the page still renders with the placeholder frame. |
| A6 | Confirmation that the three musicians are fine being named, plus the names and links. | Section 6, "Partnerships". Add the names and remove the "names pending consent" badge. | |
| A7 | Answers to the "What I learned" prompts, in Sebastián's own words (a voice note is fine). | Section 5 (`#ph-learned`). Replace the draft frame with two or three short paragraphs; remove the blue DRAFT badge. | Prompts: what broke the economy the first time and the fix; why the bag caps exist; what the ad-break payout did to the viewer count during ads; how the evolution costs were decided; what he would cut if he started over. |
| A8 | The Mix It Up command list (export or screenshot). | Optional appendix after section 3, a small "systems inventory". Not on the page yet. | |

## Facts on the page marked "to confirm"

- Launch month March 2025 (section 0 and V1).
- Version dates and change lists (section 3).
- The HOG Esports tournament list and years (section 6). The same lines carry a CONFIRM note in the CV.

## Regenerating the PDF

Serve the repository folder and print the page with headless Chrome:

```bash
python3 -m http.server 8765 --bind 127.0.0.1
```

```bash
"/Applications/Google Chrome.app/Contents/MacOS/Google Chrome" --headless=new --disable-gpu --no-pdf-header-footer --virtual-time-budget=8000 --print-to-pdf="Sebastian_Quiroga_StreamDex_CaseStudy.pdf" "http://127.0.0.1:8765/case-study.html"
```

The print stylesheet is the `@media print` block at the end of `css/case-study.css`. It is tuned for two A4 pages;
check the page count after adding the video, screenshots and quotes.
