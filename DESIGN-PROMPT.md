# SideQuest iOS App — Premium Screen Design Build

## Context

I'm building SideQuest, a group travel planning app for college students. I have 8 concept mockup screens from Replit that show the right FEATURES and LAYOUTS but look like wireframes — flat, no depth, no real photography, generic borders. I need you to rebuild each screen as a premium, high-fidelity interactive HTML file inside a realistic iPhone 15 Pro frame.

The attached images are my concept designs. Study each one carefully — preserve the feature concepts, content hierarchy, and information architecture. What changes is the VISUAL QUALITY. These need to go from "landing page wireframe" to "this could be in the App Store."

---

## Design System (USE THIS EXACTLY)

### Colors
```
--bg-primary: #0C0C0E          /* Near-black base */
--surface-1: #1A1A1E            /* Primary cards */
--surface-2: #242428            /* Elevated/nested elements */
--surface-3: #2E2E33            /* Borders, dividers, inputs */
--accent-amber: #E8923E         /* CTAs, highlights, active states, badges */
--accent-amber-glow: rgba(232,146,62,0.15)
--accent-teal: #2ECDA7          /* Success, confirmations, positive */
--accent-teal-glow: rgba(46,205,167,0.15)
--accent-coral: #E8636E         /* Reject, warnings, decline */
--text-primary: #F0F0F2         /* Headlines, primary content */
--text-secondary: #8E8E96       /* Captions, metadata */
--text-muted: #5A5A62           /* Disabled, tertiary */
```

### Typography
- Headlines: -apple-system, SF Pro Display, weight 800, tight letter-spacing (-0.5px)
- Body: -apple-system, SF Pro Text, weight 400-500
- Labels: ALL-CAPS, weight 700, letter-spacing 1.2px, size 10-11px
- Numbers/Stats: weight 800, slightly larger than surrounding text

### Depth & Shadows (CRITICAL — this is what makes it premium)
Every card uses layered shadows, NOT flat borders:
```css
/* Standard card */
box-shadow: 0 2px 8px rgba(0,0,0,0.3), 0 8px 32px rgba(0,0,0,0.2);
background: #1A1A1E;
border: 1px solid rgba(255,255,255,0.06);
border-radius: 16px;

/* Elevated card (hero moments like Group Sweet Spot, destination reveal) */
box-shadow: 0 4px 16px rgba(0,0,0,0.4), 0 12px 48px rgba(0,0,0,0.3);
border: 1px solid rgba(232,146,62,0.15);

/* Glass effect (overlays on photos) */
background: rgba(0,0,0,0.4);
backdrop-filter: blur(20px);
-webkit-backdrop-filter: blur(20px);
border: 1px solid rgba(255,255,255,0.1);
```

NEVER use flat gray borders like `border: 1px solid #333`. Always use rgba white borders at low opacity + shadows for depth.

### iPhone 15 Pro Frame (every screen uses this)
- Dimensions: 393px × 852px viewport
- Border radius: 55px on the outer frame
- Dynamic Island: 126px × 36px centered at top
- Status bar: "9:41" left, signal/wifi/battery icons right
- Home indicator: 134px × 5px bar, 8px from bottom
- Frame shadow: `0 20px 60px rgba(0,0,0,0.8)` with subtle `0 0 0 2px #2a2a2e` border

### Bottom Tab Bar (3 tabs, consistent on every screen)
- Discover (globe icon) | Trips (crossed arrows/compass icon) | Profile (person icon)
- Active tab: amber (#E8923E), filled icon
- Inactive: #5A5A62, outline icon
- Background: gradient fade from transparent to #0C0C0E
- Labels: 10px, weight 600

---

## THE 8 SCREENS TO BUILD

Build each screen as a SEPARATE .html file. Each must be inside the iPhone frame with proper status bar, dynamic island, and home indicator. Use real photos from Unsplash where indicated. Make them interactive where it makes sense (tappable states, animations, drag).

---

### SCREEN 1: swipe-vote.html — "Swipe & Vote"
**Reference: concept image showing Sagrada Familia card with X/heart buttons**

**What to keep from concept:** Tinder-style card with photo, activity name, category, X/heart action buttons, "Group Match: 4/5 agreed" indicator, trip name in header.

**What to elevate:**
- Card should be MASSIVE — take up ~60% of the screen. Not a small rectangle floating in space.
- Use a real Unsplash photo (Barcelona beach or Sagrada Familia). Photo bleeds to card edges.
- Cinematic gradient overlay on photo: bottom 50% goes from transparent to near-black. Top 20% has a subtle dark gradient for the badge.
- Card stack effect: 2 cards visible behind the main card (scaled down, slightly offset, lower opacity)
- Category info as frosted glass pills ON the photo (e.g., "🏖 Beach" "Free" "2-3 hrs")
- Activity title: 28px bold white, text-shadow for legibility
- Location line below title with a small map pin icon
- "SideQuest" badge: top-left of card, amber gradient background, uppercase 10px
- Card counter: top-right, frosted glass pill, "3 of 12"
- Action buttons below card: 3 circles — red X (60px), amber star (48px), green heart (60px). Each has a colored glow border and transparent tinted background. Scale down on press.
- Swipe indicators: "LIKE" (green, rotated 15°) and "NOPE" (coral, rotated -15°) that fade in as you drag the card
- Match toast at bottom: green-tinted rounded bar with checkmark circle + "4/5 agreed · Group match!"
- Header: back arrow + "Barcelona Trip" on left, 5 overlapping avatar circles on right (each avatar is a small emoji in a colored gradient circle, -8px margin overlap)
- MAKE IT INTERACTIVE: card is draggable left/right with rotation. Buttons trigger swipe animation.

---

### SCREEN 2: budget-lock.html — "Budget Lock"
**Reference: concept image showing member budget list, Group Sweet Spot $350, real-time splits**

**What to keep:** Member list with emoji + name + budget amount, green checkmarks for submitted, "Group Sweet Spot" hero card with per-person and total, "Real-time splits" indicator.

**What to elevate:**
- Header: back arrow + "Budget Lock" + trip name/member count below
- Member cards: dark surface cards (#1A1A1E) with proper shadows. Current user ("You 😎") gets a subtle amber left-border accent. Each card shows emoji avatar (in a small gradient circle), name, budget amount (right-aligned, bold), green check icon if submitted.
- Add a VISUAL BUDGET RANGE BAR between the member list and sweet spot. Horizontal bar showing each person's budget as an overlapping colored zone, with the sweet spot highlighted in amber. This is the key visualization.
- GROUP SWEET SPOT card is the HERO MOMENT: Larger card, amber/gold gradient border (not just orange), subtle shimmer/glow effect. Large "$350" in 40px+ bold. "per person · $1,400 total" in secondary text below. Small sparkle icon (✦) before "GROUP SWEET SPOT" label.
- "Real-time splits" row at bottom with a PULSING green dot (CSS animation), "Live" badge in green
- Add a "Lock Budget →" CTA button at bottom: full-width, amber gradient, white text, 600 weight

---

### SCREEN 3: squad-itinerary.html — "Squad Itinerary"
**Reference: concept image showing Day tabs, morning/afternoon/evening timeline**

**What to keep:** Day tabs (Day 1 active, Day 2, Day 3), three time blocks (Morning/Afternoon/Evening), activity name + "Added by [name]", drag-to-reorder hint.

**What to elevate:**
- Day tabs: horizontal scrollable row. Active tab = amber background + white text in a rounded pill. Inactive = transparent with #8E8E96 text. Each tab shows activity count: "Day 1 (3)" "Day 2 (2)" etc. Add a "+" button at the end to add a day.
- EACH ACTIVITY CARD GETS A REAL PHOTO. Use small Unsplash thumbnails (60×60px, rounded 12px) on the left side of each card. "La Boqueria Market" shows a food market photo. "Gothic Quarter Walk" shows Gothic architecture. "Sunset Viewpoint" shows a sunset.
- Time block labels (MORNING, AFTERNOON, EVENING) get color-coded left borders: Morning = warm amber, Afternoon = teal, Evening = soft coral/sunset.
- Each card shows: [photo thumbnail] | [Activity name (16px bold) + location subtext (13px muted)] | [drag handle ≡]
- "Added by" shows a tiny avatar circle + first name, not just text
- Add an EMPTY SLOT after the last filled block: dashed border card, "+" icon, "Add activity" in muted text. This communicates the itinerary is collaborative and incomplete.
- Bottom text: "Drag to reorder · Tap to edit" in 12px muted text

---

### SCREEN 4: invite-flow.html — "Who's Coming"
**Reference: concept image showing Step 1 of 4, member list with Organizer/Joined/Invited statuses, invite code BARCE-7X9K, share buttons**

**What to keep:** Step progress indicator, member list with status badges, invite code display, iMessage/WhatsApp/Copy Link share buttons, "Next: Pick Destination" CTA.

**What to elevate:**
- Step indicator: Replace "STEP 1 OF 4" text with a visual progress bar — 4 dots or segments, first one filled amber, rest unfilled. Label above: "STEP 1 OF 4" in small caps.
- Member cards with DIFFERENTIATED statuses:
  - Organizer (You): amber/gold left border, "Organizer" badge in amber
  - Joined (Sarah): green left border, "Joined" badge in teal/green
  - Invited (Jake, Priya): no left border, dimmed card, "Invited" text in muted gray
- "Add member" row: teal "+" icon in a dashed-border circle, "Add member" text, feels inviting
- INVITE CODE section: Make this feel like a TICKET or PASS. Dashed border, slightly different background (#1E1E22), "YOUR INVITE CODE" label in amber small caps. Code "BARCE-7X9K" in large monospace/bold (24px+). Copy button with amber accent.
- Share buttons: Show REAL brand colors — iMessage blue (#34C759 or the blue bubble), WhatsApp green (#25D366), Copy Link in neutral. Each in a rounded square with the icon.
- "Next: Pick Destination →" CTA: full-width, white/light background, dark text, bold. This is the primary action and should clearly stand out.
- Below CTA, add a small helper text: "Friends can join anytime with the invite code" in muted text

---

### SCREEN 5: trip-roulette-quiz.html — "Trip Roulette — Quiz"
**Reference: concept image showing 5-question quiz with energy level options**

**What to keep:** Dice emoji + "Trip Roulette" title, "Answer 5 questions. We pick your adventure." subtitle, progress bar, question card, 4 answer options with emojis, selected state, Next button.

**What to elevate:**
- Add a fun visual element at top: animated dice or globe icon with a subtle bounce/spin animation
- Progress bar: amber gradient fill with a subtle glow, show percentage text
- Question card: make it feel featured — slightly larger text (18px), maybe a subtle gradient background or a different surface level
- Answer options: dark cards with emoji + text. Unselected = standard surface. Selected = amber border + subtle amber glow + checkmark. Add a subtle scale-up animation on tap.
- "Full send 🎉" option should feel slightly different/special — maybe a subtle gradient or sparkle, since it's the most extreme option
- "Next →" button: full-width, white bg, dark text when an option is selected. Gray/disabled when nothing selected.
- Add question dots below the progress bar showing which question you're on (● ○ ○ ○ ○)

---

### SCREEN 6: trip-roulette-reveal.html — "Trip Roulette — Reveal"
**Reference: concept image showing Lisbon destination with stats and activity previews**

**What to keep:** "YOUR ADVENTURE AWAITS" header, flag emoji, "Lisbon, Portugal", stats (5 Days, $1,800, $450/person), "Great match for your group's vibe", activity previews (Alfama, Cervejaria Ramiro, Cascais), Spin Again / Let's Go buttons.

**What to elevate:**
- THIS SCREEN NEEDS A HERO PHOTO. Use a beautiful Unsplash photo of Lisbon (Alfama rooftops, tram 28, or river view). It should take the top 40% of the screen with a gradient fade to the dark background.
- Stats overlay: frosted glass card floating OVER the bottom of the hero photo. Three stat columns (5 Days | $1,800 total | $450/person) with thin dividers.
- "Great match for your group's vibe" → change to "94% match for your group's vibe" with a small star icon. Feels more concrete.
- Activity preview cards: MUST have thumbnail photos, not just emoji icons. Each card shows a small photo (48×48 rounded), activity name, and category label (Local Pick in teal, SideQuest in amber, Adventure in coral).
- "Let's Go! 🚀" = primary CTA, full-width, amber gradient background, white bold text, prominent
- "Spin Again" = secondary, ghost/outline style, sits next to or above Let's Go
- Add a subtle confetti or sparkle animation on page load to make the reveal feel celebratory

---

### SCREEN 7: budget-settlement.html — "Budget Settlement"
**Reference: concept image showing Trip Complete, total spent, who-owes-who cards**

**What to keep:** "Trip Complete!" with party emoji, total spent with progress bar and "Under budget!" badge, settlement rows (Jake→Sarah $47.50, You→Jake $23.00, Sarah→You $12.25), Settle/Request buttons, "Powered by SideQuest+".

**What to elevate:**
- Celebration header: party emoji LARGER (48px), maybe a subtle confetti animation in the background, or gold/amber particles
- Total spent card: hero card treatment with green accent (since under budget). Progress bar should be GREEN with a satisfying fill animation. "$2,247" in large bold. "of $2,400" in muted. "Under budget! 🎉" badge in green.
- Settlement cards: each shows BOTH avatars (sender → receiver) as small emoji circles with an arrow between them. Amount is bold and right-aligned. 
  - "Settle" button = green/teal filled, for debts YOU owe
  - "Request" button = amber outline, for money owed TO you
  - Already settled rows get a "✓ Settled" muted badge
- "Settlements powered by SideQuest+" at bottom: subtle, premium feeling, maybe a small sparkle icon. This hints at the premium tier.
- Add a "Share Summary" link at the very bottom in muted text — users would want to send this to the group

---

### SCREEN 8: profile.html — "Profile & Gamification"
**Reference: concept image showing avatar, Gold Explorer rank, XP bar, stats, country stamps, badges**

**What to keep:** Avatar circle with initial, "Hadi M." name, "Gold Explorer" rank, XP progress bar (2,450 / 5,000), stat cards (4 Trips, 12 SideQuests, 3 Countries), country stamps as flags, badge grid (Early Adopter, Budget King, etc.)

**What to elevate:**
- Avatar: gradient circle (amber → coral), "H" initial in white bold. Add a subtle glow/ring effect. Later this becomes a photo.
- "Gold Explorer" rank: use a subtle gold/metallic gradient on the text, with a small crown or rank icon. Make it feel EARNED.
- XP bar: amber gradient fill with a glow. Show rank tiers as subtle markers along the bar. "2,450 XP" left, "5,000 XP to Platinum" right.
- Stat cards: 3 equal columns in a card row. Each has: large bold number (24px), label below in small muted caps, and a small icon above the number (✈️ for trips, ⚡ for sidequests, 🌍 for countries). Cards have proper shadows and surface treatment.
- Country stamps: flag circles (32px) with a subtle border ring. The "+" button for adding countries should feel inviting. Maybe add a subtle pulse animation on the "+" to encourage engagement.
- Badge grid: THIS NEEDS PERSONALITY. Each badge should feel like a collectible:
  - Earned badges: full color emoji/icon, name below, subtle glow or elevated treatment
  - Unearned/locked badges: grayscale, dimmed to 30% opacity, "Locked" text or lock icon overlay
  - Make each badge a different subtle color accent (gold for Early Adopter, green for Budget King, blue for Jet Setter, etc.)
- Add a "Recent Trips" section below badges: 1-2 horizontal cards with small Unsplash photos + trip name + date. This adds visual storytelling to an otherwise stats-heavy screen.

---

## GLOBAL RULES

1. **Every screen is a separate .html file** with the full iPhone frame, status bar, dynamic island, and home indicator.
2. **Use real Unsplash photos** wherever photos are needed. Use direct URLs with ?w=800&q=80 for performance.
3. **Animations should be subtle and purposeful**: entry animations (fade + slide up), progress bar fills, hover/active states, toast slides. No janky or distracting motion.
4. **Accessibility**: all interactive elements should have cursor:pointer. Buttons should have active states (scale 0.95 on press).
5. **NO flat gray borders**. Every card uses shadows + rgba borders for depth.
6. **Consistent spacing**: 20px horizontal padding for screen content, 16px between cards, 12px between elements within cards.
7. **Each file should work standalone** — open it in a browser and see the full iPhone mockup.
8. **Make it PREMIUM**. Think Airbnb production quality meets Nike SNKRS dark mode energy. If something looks like a wireframe, it's not done yet.

---

## FILE OUTPUT

Create these 8 files:
1. `swipe-vote.html`
2. `budget-lock.html`
3. `squad-itinerary.html`
4. `invite-flow.html`
5. `trip-roulette-quiz.html`
6. `trip-roulette-reveal.html`
7. `budget-settlement.html`
8. `profile.html`

Start with swipe-vote.html and work through them in order. After each screen, stop and let me review before moving to the next one.
