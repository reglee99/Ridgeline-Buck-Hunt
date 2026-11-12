# Ridgeline Buck Hunt

An arcade-style deer hunting game that runs in the browser. You get three hunting sites with 75 seconds each to tag as many bucks as you can. Some deer are out to 270 yards, so you'll need the scope for the far ones. Don't hit the does.

The whole game is one HTML file. It has no build step, no dependencies to install, and no server.

## Play

Open `index.html` in any modern browser, or play the hosted version on GitHub Pages (see [Hosting](#hosting)).

## Controls

| Action | Mouse and keyboard | Touch |
| --- | --- | --- |
| Aim | Move the mouse | Tap where you want to shoot |
| Shoot | Left click | Tap |
| Scope (4×) | Hold Shift, or press Z to toggle | Not available |
| Reload | Right click, Space, R, or the Reload button | Reload button |
| Help (pauses the hunt) | H or the Help button; Esc closes it | Help button |
| Full screen | Full screen button | Full screen button, where the browser supports it |

The game fills the browser window. The Help button opens the controls, ballistics and scoring notes.

## The sites

1. **Cold Creek Ridge:** dawn, 28°F, frosted grass and evergreens.
2. **Hickory Hollow:** midday, 46°F, autumn hardwoods and leaf litter.
3. **Whitetail Flats:** dusk, 14°F, light snow. The deer move fastest here.

Deer keep coming for the full 75 seconds at each site. They walk, stop to feed, go on alert, and bolt as soon as you fire.

## Ballistics

- The rifle is zeroed at 100 yards. It hits about 4 inches low at 200 yards and 14 inches low at 300. The scope reticle has hold marks for 200 and 300.
- The scope shows the range to whatever is under the crosshair.
- Shots land where the crosshair is when you fire, so you don't need to lead running deer.
- Recoil lifts the muzzle after each shot, and the aim sways slightly.
- Tree trunks stop bullets.

## Scoring

| Event | Points |
| --- | --- |
| Buck tagged | 100 per antler point (6 to 12 points) |
| Range | 2 per yard |
| Heart-lung shot | +500 |
| Head shot | +250 |
| Neck shot | +150 |
| Quick draw (within 2.5 s of the buck appearing) | +200 |
| Running shot | +250 |
| Accuracy bonus at the end of each site | Up to +500 |
| Clean hunt (bucks tagged, no does hit) | +500 |
| Doe hit | −500 |

A gut or leg shot only wounds a buck. It runs, and you have to hit it again before it leaves the screen.

Your final rank depends on your total across all three sites:

| Score | Rank |
| --- | --- |
| 45,000+ | Legend of the Ridge |
| 30,000+ | Trophy Hunter |
| 18,000+ | Sharpshooter |
| 8,000+ | Meat Hunter |
| Below 8,000 | Greenhorn |

Your best score is saved in your browser's local storage.

## Hosting

To host the game with GitHub Pages:

1. Push `index.html` to the repository.
2. In the repository, go to **Settings → Pages**.
3. Under **Build and deployment**, choose **Deploy from a branch**, then select your main branch and the root folder.
4. Save. After a minute or two the game is live at `https://<your-username>.github.io/<repository-name>/`.

## How it's built

- Everything is drawn on an HTML canvas with plain JavaScript. There are no images or game libraries.
- The scenery is generated from a fixed seed for each site, so every site looks the same each time you play it.
- Sound is synthesized live with the Web Audio API. Browsers only allow audio after you interact with the page, so the sound starts after your first click.
- The fonts load from Google Fonts. Without a connection the game falls back to system fonts and still plays.
