# sobriquets

Repository for my [Sobriquets](https://jamescalixto.com/site/wp-content/uploads/media/sobriquets/main.html) project. Check it out!

## Background
My friends and I are big fans of [Codenames](https://boardgamegeek.com/boardgame/178900/codenames), a team board game where you try to pick out your team's words based on hints. (It's hard to explain, read the game rules for more!)

Nothing about Codenames is particularly difficult to code, and it can be implemented in JavaScript fairly easily. Thus I decided to create an implementation myself, which I named Sobriquets.

## Design decisions and other notes
### Local multiplayer only
While having actual rooms and synchronized browser gameplay would be nice, it was prohibitively technically difficult to implement and also defeats the point of Codenames. The point of the game may be to win, as my high school gym teacher loved to say, but on a higher level it's to enjoy the company of other people. Codenames is best played in-person, and I wanted my implementation to facilitate in-person gameplay rather than supplant it.

### Synchronization
I used something slightly more sophisticated than the honor system to ensure synchronization. Namely, the random seeds are designed to synchronize everyone's boards while still ensuring some level of secrecy on the part of the spymasters. Thus, there is one public seed so that everyone has the same board, but there is a private seed for the spymasters to get their identities.

To ensure a novel stream of boards, I hash these seeds with an appropriate time interval so that using the same seeds about three hours apart gives a new board and identities. Otherwise, common seeds might recur enough to become predictable.

Slight quirk of my implementation: the number of red/blue cards is actually determined by the public board seed and not the private identity seed. This way, everyone has a counter of how many cards are left. The downside is that the same board will have the same team going first for periods of three hours; this is a small price to pay for the convenience and is easily mitigated by choosing a different seed.

### Visual design
I am using the same slightly rounded rectangle aesthetic that I have honed over my previous two projects ([here](https://github.com/jamescalixto/wing-menu-optimization) and [here](https://github.com/jamescalixto/washington-post-now-headlines)), but further refined. I am also using a nicely expanded color palette courtesy of some online palette generator.

The combination of Playfair Display, PT Serif, and Roboto continues to look great; I may overhaul my main website to utilize this triad.

When designing the responsive layout for narrower phones, I realized that there was no particular reason why the board needed to be 5x5 aside from aesthetics. Thus at narrow widths the board becomes 3x8. I also toyed with the idea of creating a checklist mode, which would be less visually pleasing but far easier to work with as the spymaster. I did not end up implementing this but only due to the 3x8 layout being sufficient.

## Directories and files
### `data`
Holds the `default.txt` file, a word list from [this website](https://www.horsepaste.com/). 

### `img`
This directory holds the favicon for the page.

### `main.html`, `main.js`, `styles.css`
These three files make up the main body of the project and are the visible segments of [the project](https://jamescalixto.com/site/wp-content/uploads/media/sobriquets/main.html).