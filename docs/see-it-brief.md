# /see-it page · structure, design, content and build notes

**Nov 18, 2026 · v3 DRAFT for Onkar's review.** Once approved, hand this file and the HTML to Ayush or Inaam to build in GHL.

**What changed in v3:** every video is a YouTube embed that plays on the page; phone layout reworked (one video per row, video right under each heading, "Show more" for long rows); page size down from 1.1 MB to 250 KB.

**What changed in v2:**
- Added the long-form build video.
- Added the explainer ad.
- Added Finley's note.
- Added an "Up close" section of detail Shorts.
- Added two Instagram reels and two more Meta reels.
- Fixed the "Video unavailable" error in the preview.

**Files**
- This brief.
- [ghl-custom-code.html](../ghl-custom-code.html): the paste-ready code for one GHL Custom Code element.
- [page.html](../page.html): the same page, to open in a browser.

**Where the content decisions come from**
- Pages doc, page 11 and decision P4.
- The research bank there (section 5a, the video list; 5b, their own language).
- The messaging plan, which lists the Finley-approved ad videos, including the explainer.
- The page-list decision that "the shop videos and Finley's note go on `/see-it`" (no separate shop page).
- The approved emails that link here: W14 "Under the paint", W15 Emails 3–4 and W17 Q5.

---

## 1. What the page is

| | |
|---|---|
| **Job** | Get a lead excited between messages: the build, the details, the owners, delivery day. Then send them to the meeting with Trey |
| **Who lands here** | Leads already in the pipeline, from email and text buttons. Not ad traffic |
| **Page type** | One step in the existing `build.golfingarage.com` funnel, built like the Build Book page: a single Custom Code element in the live dark "showroom" template (same header, footer, fonts and colors). No form |
| **URL** | `https://build.golfingarage.com/see-it` |
| **The one action** | **Pick a Time With Trey** → `/design-meeting` (the free calendar, link L1), carrying the email's UTMs through |
| **Search** | Hide from search (noindex) |

## 2. One page or several?

**One page, with lots of videos, grouped into sections.** Each message links straight to the section it promises:

| Jump link | Section | Linked from |
|---|---|---|
| `/see-it#frame` | The build | W14 "Under the paint", W15 Email 4, W17 Q5 |
| `/see-it#whole-story` | The 11-minute build video | Available for nurture later |
| `/see-it#details` | Up close | — |
| `/see-it#shotgun` | For whoever rides with you | W15 Email 3 |
| `/see-it#delivery` | Delivery day | — |
| `/see-it#around-town` | Out and about | — |

**Why more videos make sense here:**
- People only come to this page to watch, so more good footage means more reasons to get excited.
- Grouping keeps it easy to scan. The jump links at the top show how many videos each section has.

**Why one page, not several:**
- Only a few dozen email and text clicks a month reach it, too few for an A/B test.
- One page means one place to update.
- Booked and not-booked leads see the same page. One line under the main button covers booked leads.

## 3. Structure (top to bottom)

| # | Block | What's on it | Plays today? |
|---|---|---|---|
| 0 | Header | Logo, phone, **Pick a Time With Trey** | — |
| 1 | Opening | Headline, one line, 7 jump links with video counts | — |
| — | Meet Trey | Trey's intro clip | Hidden until the clip exists |
| 2 | `#frame` 01 The build | Frame, body and paint copy · main video · 4 shop Shorts · 4 build facts | **Yes** (5 Shorts) |
| 3 | `#whole-story` 02 The whole story | **The long-form video** (10:59), full width · the explainer ad below it | **Yes** (long-form) |
| 4 | A note from the owner | Finley's note on why they build by hand | Hidden until Finley approves it |
| 5 | `#details` 03 Up close | 6 detail Shorts (seats, lights, stance, frunk) | **Yes** |
| 5b | `#colors` 04 Your color | 4 color Shorts · "bring a color idea" | **Yes** |
| 6 | `#shotgun` 05 For whoever rides with you | Spouse video + "didn't tell husband" · "Pick a Time for Both of You" | When they're on YouTube |
| 7 | `#delivery` 06 Delivery day | Customer delivery video | When on YouTube |
| 8 | `#around-town` 07 Out and about | 4 Meta reels + 2 Instagram reels | When on YouTube |
| 9 | Facts strip | 100+ since 2020 · Jasper, GA · VIN · lower 48 | — |
| 10 | Closing call to action | "Design Yours With Trey" · button · booked line · phone | — |
| 11 | Footer + phone bar | The live template's footer and sticky phone bar | — |

**On launch day,** with only the YouTube videos, the page shows 4 sections and 16 videos. Each video added to YouTube makes its section appear.

## 4. Design

**Same look as the live pages.** The HTML reuses the Build Book page's own code, the V2 "charcoal automotive showroom" dark theme. Header, footer and fonts are copied unchanged.

| Element | Spec (from the live pages) |
|---|---|
| Background | Charcoal `#171A1A`; bands `#202424`; video backgrounds `#101313` |
| Text | Off-white `#F3F1ED`; secondary `#B7BDBB` |
| Accent | Orange `#E37125` (buttons, section numbers, play buttons) |
| Headings | Barlow Condensed 700, uppercase |
| Body | DM Sans; labels in JetBrains Mono uppercase |
| Buttons | Square corners, orange fill, dark text |

**Video players:**
- **Shape.** Reels and Shorts play in vertical 9:16 frames. The long-form video plays full width in 16:9, up to 1,100 px. Each card has a `data-ratio` setting to match its file.
- **YouTube embeds with our own cover.** Every video is a YouTube player on the page. Before it plays, a cover with the video's thumbnail and our orange play button sits over YouTube's start screen, so the red Shorts logo and title bar don't show. The tap goes straight through to YouTube's player, so it plays with sound on phones. The cover comes back when a Short pauses or ends, which also hides YouTube's "more videos" screen. While a Short is playing, YouTube still shows its small Shorts label and like/share buttons; no embed setting removes those. Nothing autoplays, and players lower on the page load only as the visitor scrolls to them. Starting one video pauses the others.
- **Each card shows** the player and a caption.
- **Phones:** one video per row, about 340 px wide. In each section the video comes right after the heading and opening line, before the fact list and button. Rows with more than 2 videos show 2, then a "Show more videos" button.
- **Grid.** 4 per row on desktop, 3 on tablet, 1 on a phone.
- **No empty players.** A card with no YouTube ID stays hidden. A section with no videos hides itself and its jump link.

**About the "Video unavailable" message:**
- YouTube refuses to play inside a page opened as a file on a computer (Error 153). That's what the preview file did.
- It isn't a problem with the videos. YouTube confirms all seven allow embedding on other sites.
- Every video plays on the page itself, with no jump to YouTube. Review it on the GitHub Pages link or the live site. A copy opened as a file on your computer will still show the YouTube error.

## 5. Content (final copy, copy checker clean)

**Page title:** See It | Golfin' Garage
**Meta description:** Short videos from the Golfin' Garage shop in Jasper and from Retro Ride owners.

**Opening**
- **Label:** See it · from the shop and our owners
- **H1:** From Bare Steel to Your Driveway.
- **Line:** Short videos from our Jasper shop and from the people who drive theirs. Start with the one you came for.

**Meet Trey** (hidden until the clip exists)
- **H2:** The Person Who Designs Yours.
- **Copy:** In 30 minutes on video, Trey designs yours with you, one choice at a time.

**01 · The build** (`#frame`)
- **H2:** Built From the Frame Up.
- **Copy:** Every Retro Ride starts as straight steel tube that we cut, bend and weld in our Jasper shop, then powder-coat twice and set on independent suspension. The fiberglass body is laid by hand and painted in PPG paint mixed to the color you pick. Nobody else gets that build.
- **Facts:**
  - Steel frame welded in our shop
  - Hand-laid fiberglass body
  - Diamond-stitched marine-grade vinyl seats
  - A VIN and a manufacturer's certificate of origin
- **Main caption:** "From bare frame to finished Retro Ride." Until the chassis reel is on YouTube, the slot plays "Building the beast" with "Building one in our Jasper shop."

**02 · The whole story** (`#whole-story`)
- **H2:** One Build, Start to Finish.
- **Copy:** If you have eleven minutes, follow one Retro Ride across our shop floor, from bare steel to the finished ride. This one was built against a deadline; yours gets its own timeline, set when you place your order.
- **Captions:**
  - "One build, start to finish, on our shop floor."
  - "The Retro Ride, explained."

**A note from the owner** (DRAFT, hidden until Finley approves or rewrites it)
> Since 2020 we've built more than 100 Retro Rides in our Jasper shop, and we still build every one the same way: the frame welded here, the body laid by hand, the paint mixed to one owner's color. When yours leaves the shop, there won't be another one like it.
> Finley, owner, Golfin' Garage

**03 · Up close** (`#details`)
- **H2:** It's in the Details. (their own brand line)
- **Copy:** The vintage dash we build ourselves, the diamond-stitched seats, the trim and the lights. Every detail on these was picked by its owner.

**04 · Your color** (`#colors`)
- **H2:** Pick Your Color.
- **Copy:** Paint is one of the first things you'll choose with Trey: any color, including custom two-tone. Bring a photo, a paint chip or an old truck you loved. (From the live prep page.)

**05 · For whoever rides with you** (`#shotgun`)
- **H2:** Show the Person Riding Shotgun.
- **Copy:** Most Retro Rides get decided by two people. If yours includes someone who isn't sold yet, start them here.
- **Button:** Pick a Time for Both of You · *Each of you can join from your own phone.*

**06 · Delivery day** (`#delivery`)
- **H2:** The Day It Comes Home.
- **Copy:** We deliver anywhere in the lower 48. This is one owner's delivery day, start to finish.

**07 · Out and about** (`#around-town`)
- **H2:** Where Retro Rides Get Driven.
- **Copy:** The coffee run, the neighborhood loop and the ride down to the dock. Every one of these was built to order for its owner.

**Facts strip:** 100+ / Retro Rides built since 2020 · Jasper, GA / Built by hand in our shop · VIN / And a certificate of origin with every build · Lower 48 / We deliver anywhere

**Closing**
- **H2:** Design Yours With Trey.
- **Copy:** In 30 minutes on video, Trey goes through your build with you, one choice at a time, from the paint to the seats. You leave with every choice made and the price for exactly that build.
- **Button:** Pick a Time With Trey
- **Under the button:** Already booked? Your Google Meet link is in your confirmation email. See you there.
- **Phone line:** Rather talk now? Call (706) 253-4040.

**Rails kept:**
- No golf, Ford/Bronco, holiday, discount, financing, speed or fixed build-time claims.
- No rendering language.
- Facts come only from the approved list or from approved W14, W15 and W4 copy.

## 6. Videos (28 slots)

| Section | Video | Source | Length | Status |
|---|---|---|---|---|
| Meet Trey | Trey's intro | Not filmed yet (L6) | ~1 min | Need |
| `#frame` main | Chassis Underneath ("Retro on the outside. Built for right now underneath.") | Meta 1108787821511122 | 0:58 | Needs to go on YouTube. A Short stands in |
| `#frame` row | "Building the beast!" | YouTube Short e6LHUT7vmLg | short | **Live** (hidden while it's also the main) |
| `#frame` row | "Inside Golfin' Garage!" (frame welding) | YouTube Short 70vpA8iqhw4 | 0:12 | **Live** |
| `#frame` row | "Take a look inside the lab!" | YouTube Short leG8iir3a-s | 0:13 | **Live** |
| `#frame` row | "Work inside the garage!" | YouTube Short WuSkZReuBss | 0:12 | **Live** |
| `#frame` row | "Final checks!" | YouTube Short 7-uFf0sgVxs | 0:06 | **Live** |
| `#whole-story` | **"You Won't Believe What We Built In 4.5 Days…"** (long-form) | YouTube vG8f0bwUCB4 | 10:59 | **Live**, see D2 |
| `#whole-story` | The explainer ad (Ayush's "Vox-style explainer") | Ayush's file | ? | Needs to go on YouTube |
| `#details` | "Built in the Details" | YouTube Short ljUXkyBdvUQ | 0:13 | **Live** |
| `#details` | "Simple. Refined. Ready." (seats) | YouTube Short qgl14S7Sqmk | 0:07 | **Live** |
| `#details` | "Lights on, presence felt!" | YouTube Short Jw5jFrpamRg | 0:13 | **Live** |
| `#details` | "Strong stance, clean details!" | YouTube Short UoNWxlUGOKA | 0:11 | **Live** |
| `#details` | "Custom-built frunk!" | YouTube Short wBDTEAbmXnU | 0:12 | **Live** |
| `#details` | "Luxury on wheels!" | YouTube Short HTAgd3wvQF8 | 0:14 | **Live** |
| `#colors` | "Different colors, which one are you taking?" | YouTube Short 9ovWiJvatQ4 | 0:17 | **Live** |
| `#colors` | "Yellow beast!" | YouTube Short icWAkbUZWFw | 0:11 | **Live** |
| `#colors` | "You've never seen 'Yellow' like this!" | YouTube Short mqpGIenx9Gs | 0:11 | **Live** |
| `#colors` | "Choose your weapon!" | YouTube Short BRnIihdMCB8 | 0:12 | **Live** |
| `#shotgun` | Spouse video ("she won't stop riding in it") | Meta 1147298017532819 | 0:35 | Needs to go on YouTube |
| `#shotgun` | "Didn't tell husband" UGC | Meta 2764338840652081 | 0:17 | Needs to go on YouTube |
| `#delivery` | Customer delivery, subtitled | Meta 4379996238906952 | 1:11 | Needs to go on YouTube |
| `#around-town` | Coffee Shop | Meta 1053683347351822 | 0:16 | Needs to go on YouTube |
| `#around-town` | "The Truck You Grew Up Wanting" | Meta 1111645881789816 | 0:16 | Needs to go on YouTube |
| `#around-town` | "The neighborhood loop just got a serious upgrade." | IG reel Df0FfxKjBAi | short | Needs to go on YouTube |
| `#around-town` | "Life's too short for a cart that looks like everyone else's." (21.9K likes) | IG reel DdjpZXMjAdo | short | Needs to go on YouTube; check no badges show |
| `#around-town` | "Any hobby gets 10x better" | Meta 2180767295834515 | 0:12 | Needs to go on YouTube |
| `#around-town` | "Some decisions are easy" | Meta 1718440376042520 | 0:10 | Needs to go on YouTube |

**Left off on purpose:**

| Video | Why |
|---|---|
| Shorts with a licensed song: "Luxury from every angle!" (xrmbkT2kpQk, "Aces" by dkj), "Finished the right way!" (At5PfblPGMU), "Before & After" (iQoCyE7QB-U), "Red or White?" (qh0VUz1jebY), "Gloss Black Color" (R18xF6Ak6AQ) | Same music risk as below. Each has a song credited on YouTube |
| "Inside Golfin' Garage!" (YouTube Short vXPJgSgycCI) | Its soundtrack is a commercial song (Yeat, "COME N GO"). YouTube can block songs like that from playing on other websites, by country or device, and the player then shows "Video unavailable". **Rule for every video on this page: no licensed music.** Ask Rabih for a version with no music or the original audio |
| "Golfin' Garage Retro Ride" Q&A (YouTube YbWxbvOPjys, 3:00; the hidden "film" on the landing page) | Shows a Porsche and says "47 or 48 mph." Kept for research only |
| "Bronco Dream" ads, the GolfCartingTV shop tour, Bronco-titled Shorts | The Bronco name |
| "Red beast unleashed!" (5YW6mdWQ9eY), "Clean. Sharp. Untouchable." (wOHhuCgCZ9Y) | Grille and body read as a Bronco. Could be added after a check |
| PGA Show vlog, "Inside Velocity Restorations" | Golf event; "classic Ford 4x4s" |
| Holiday "Build Sheet" video, "Already Spoken For" trailer | Holiday deadline; dated scarcity |
| "You Can Pour WHAT Out Of This Cart??" (Vintage Bar Co., 14:43) | Fits a business audience only. Save it for the business branch |

**Before any video goes up, someone watches it all the way through.** Check for:
- Bronco or Ford names, golf courses, holiday deadlines, financing.
- A spoken speed or a build-time promise.
- A commercial song in the soundtrack. After uploading, check YouTube Studio → Copyright for a claim; a claimed song can make the video unavailable on this page.

The research lists these as client-approved or their own posts, but I haven't watched them end to end.

**Thumbnails:** YouTube's own. Set a good custom thumbnail on each video in YouTube Studio when it's uploaded.

## 7. Building it in GHL (Ayush / Inaam)

1. In the `build.golfingarage.com` funnel, add a step with the path `see-it`.
2. Add **one Custom Code element**, full width, the same as the Build Book page, and paste in the whole HTML file.
3. **Page settings:**
   - **Title:** See It | Golfin' Garage
   - **Meta description:** as in section 5
   - **Search indexing:** off
   - Keep the funnel's tracking code in the head.
4. **Videos:**
   - **Get them onto YouTube.** Download each Meta video (Meta Business Suite → Media library) and each Instagram reel, and upload them to the Golfin' Garage YouTube channel. Unlisted is fine: unlisted videos still embed.
   - **Fill in each card.** In the code, each card is `<div class="gg-vid" data-yt="" …>`, with a comment above it naming the video. Put the 11-character YouTube ID (the part after `v=` or `/shorts/`) into `data-yt`, and set `data-ratio` (`9/16` for Shorts and reels, `16/9` for wide videos).
   - **Chassis reel.** Once it's on YouTube, put its ID in the `#frame` main card and update its caption.
5. **Trey's clip and Finley's note:**
   - **Trey's clip** shows itself once its `data-yt` is filled.
   - **Finley's note** shows when the word `hidden` is removed from its section. Only after Finley approves the wording.
6. **Publish, then test on a phone:**
   - Every jump link lands on its section, and videos play.
   - The phone bar shows.
   - "Pick a Time" opens `/design-meeting` with the UTMs.
   - Then run the funnel QA check before telling the team it's live.

## 8. Links to switch once it's live

| Message | Button | Today | After publish |
|---|---|---|---|
| W14 "Under the paint" | Watch a frame become a Retro Ride | YouTube Short | `/see-it?utm_source=ghl&utm_medium=email&utm_campaign=w14-paint#frame` |
| W15 Email 4 | Watch a frame become a Retro Ride | YouTube Short | `/see-it?…&utm_campaign=w15-e4#frame` |
| W17 Q5 | Watch a frame become a Retro Ride | YouTube Short | `/see-it?…&utm_campaign=w17-q5#frame` |
| W15 Email 3 | Watch the story (35 seconds) | Dropped | `/see-it?…&utm_campaign=w15-e3#shotgun`, **once the spouse video is on YouTube** |

The `#` jump always goes **after** the UTMs.

## 9. Decisions for Onkar

| # | Question | My recommendation |
|---|---|---|
| S1 | One page, many videos in sections, no variants? | **Yes** |
| S2 | Every button goes to `/design-meeting` (free calendar)? | **Yes** |
| S3 | Go live with the YouTube videos (4 sections, 16 videos), and let the rest appear as each one goes on YouTube? | **Yes** |
| D2 | The long-form video: the earlier decision was to cut out its PGA Show mentions first. Use the full YouTube video now, or wait for Rabih's cut? | **Use it now, with the "built against a deadline" line**, and swap in the cut when it's ready. Say no if any PGA mention is a deal-breaker |
| D3 | Finley's note: send the draft to Finley to approve or rewrite? | **Yes.** It stays hidden until Finley answers |
| S4 | Copy in section 5? | Approve or mark up |
