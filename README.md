# TwentyFour Web Games

A set of four lightweight, self-contained browser games built for the TwentyFour website (twentyfour.store). Each game is a single HTML file with its own styles and script. There are no frameworks, no external libraries and no build step.

## Games

| File | Game | Type | Goal |
|---|---|---|---|
| `twentyfour-cap-catch.html` | **Cap Catch** | Arcade (canvas) | Catch falling caps in the "24" crate. Each cap style scores different points. Miss 3 and it's game over. |
| `twentyfour-cap-dash.html` | **Cap Dash** | Endless runner (canvas) | Jump needles and crates, collect coins, survive as the speed keeps rising. |
| `twentyfour-reseller-academy.html` | **Reseller Academy** | Educational quiz | Serve 10 customers by answering reseller and product questions before the timer runs out. |
| `twentyfour-branding-match.html` | **Brand It!** | Educational matching | Match each branding method to its look, its description and the job it suits best. |

## Controls

| Game | Desktop | Mobile |
|---|---|---|
| Cap Catch | Mouse or `←` `→` keys | Drag a finger |
| Cap Dash | `Space`, `↑` or `W` (hold for a higher jump) | Tap (hold for a higher jump) |
| Reseller Academy | Click an answer | Tap an answer |
| Brand It! | Click a name, then its match | Tap a name, then its match |

## Adding a game to the website

### WordPress (including Avada)
1. Create or edit the page where the game should appear.
2. Add a **Code Block** element (in Avada Builder) or a **Custom HTML** block (in the block editor).
3. Open the game's `.html` file in a text editor, copy **everything**, and paste it into the block.
4. Save and preview the page.

Each game is wrapped in its own `<div>` with its own ID, so more than one game can be placed on the same page, or all four on separate pages, without conflicts.

### Any other site or standalone use
- Paste the file's contents into any HTML page, or
- Upload the `.html` file and open or embed it directly (for example with an `<iframe>`).

## Fonts and colours

- **Font:** all games request `Modelica`, with a fallback to Helvetica and Arial. Modelica is a licensed font, so the games only display it if the website already loads it (for example through the theme). If it isn't loaded, visitors see the fallback font. Ask your web developer to add the Modelica font files if needed.
- **Colours:** the brand colours are 100% CMYK yellow (`#FFED00` on screen), charcoal (`#1A1A1A`) and a pale yellow background (`#FFF9DB`). Each game's CSS variables sit at the top of the `<style>` block. The two canvas games (Cap Catch and Cap Dash) also hold the same colours as constants near the top of the `<script>`, so change them in both places.
- The red, green, blue and purple used for cap styles and answer feedback are in the scripts and can also be edited.

## Editing the content

| Game | Where to edit | What you can change |
|---|---|---|
| Cap Catch | `TYPES` list in the script | Cap styles, points, how often each appears, colours |
| Cap Dash | Constants near the top of the script (`G`, `JV`) and the `update` function | Gravity, jump strength, speed ramp |
| Reseller Academy | `Q` list in the script | Customers, questions, answers and the "did you know" tips. **The first option in each question is always the correct one**, and the game shuffles them. |
| Brand It! | `T` list in the script | Branding names, descriptions and "best for" clues |

## Scores and privacy

- Each game saves the player's best score in the browser using `localStorage`. Nothing is sent to a server, and no personal information is collected.
- If a browser blocks storage (for example in private mode), the games still work but won't remember the best score.

## Content accuracy

The educational content was written from information on twentyfour.store, including the product categories, lead times, sample process and branding methods. Business details such as prices, lead times and stock policies change, so:
- Have a TwentyFour team member review the questions and descriptions before publishing and again after any policy change.
- The branding descriptions in Brand It! are general industry explanations, not wording taken from the website. Check them against what TwentyFour offers.
- No rand prices or set-up fees are used in any game, because the website's pages listed different figures.
- The end screens link to `https://twentyfour.store/find-a-store-or-reseller/` and `https://twentyfour.store/branding/`. Confirm these links work, or edit them in the file.

## Compatibility

Works in current versions of Chrome, Edge, Firefox and Safari on desktop and mobile. The canvas games scale to the width of their container (up to about 420px for Cap Catch and 760px for Cap Dash). The quiz and matching games adapt to small screens and respect the "reduce motion" accessibility setting.

## Troubleshooting

| Problem | Likely cause and fix |
|---|---|
| The game shows as plain text or code | The page builder stripped the HTML. Use a Code Block or Custom HTML block, not a text or paragraph block. |
| Keyboard keys scroll the page | Click the game once to focus it. Cap Dash and Cap Catch block scrolling only while a game is running. |
| Wrong font | Modelica isn't loaded on the page. See the Fonts and colours section above. |
| Buttons look different | A theme's CSS may override button styles. Each game scopes its styles to its own container, but you can add `!important` to any rule that is being overridden. |
| Best score not saved | The browser is blocking `localStorage`. |

## Ideas for the future

- A leaderboard or a "score for a discount code" prize (needs a small server or plugin to be trustworthy).
- Duck-under obstacles and unlockable cap skins in Cap Dash.
- A "customer brief" round in Reseller Academy that matches budget and order size to the right branding option.
