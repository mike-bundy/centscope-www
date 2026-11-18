# CentScope Marketing Website

A static marketing website for the CentScope financial wellness platform, built with Tailwind CSS.

**Status: pre-launch.** CentScope is coming soon to iOS, Android, and the web. The site says so throughout and deliberately has no sign-in, sign-up, demo, or store links. Nothing on it points at the app backend yet.

## Pages

1. **index.html** - Main landing page with Members / Institutions / Community toggle
2. **about.html** - About page with mission, values, launch facts, and team
3. **name-research.html** - Internal naming research from the Rise → CentScope rebrand. Not linked from the site.

## Design System

### Colors

Sampled from the CentScope logo:

- **cs-blue** `#4879a4` - The "Cent" blue. Primary: buttons, links, active toggle
- **cs-sky** `#8abee3` - The "Scope" light blue. Accents and icon tiles
- **cs-sun** `#f7e769` - Pinwheel yellow. Buttons and highlights on dark backgrounds
- **cs-lime** `#cbd25d` - Pinwheel green. Icon tiles, end of the citrus gradient

Derived from the logo blue to round out the palette:

- **cs-navy** `#1f3a56` - Headings, footer, dark sections
- **cs-mist** `#eaf3fa` - Background neutral
- **cs-slate** `#3d4b5a` - Body text

Sky, sun, and lime are too light to carry white text. Put navy text and icons on them; keep white text for blue and navy.

Three section backgrounds are defined in each page's `<style>` block: `bg-brand-blue` (blue gradient), `bg-brand-navy`, and `bg-brand-citrus` (yellow → lime). Each layers the plus-sign texture over the colour.

### Logo files

- `logo.png` - Full-colour wordmark, for light backgrounds
- `logo-reversed.png` - "Cent" in white, for dark backgrounds (the footer)
- `mark.png` - The pinwheel on its own. Use it on white, mist, or navy; its petals disappear on yellow or blue
- `favicon.png` - The pinwheel at 96px

These were cut from a screenshot of the logo. Swap in proper vector exports when they're available.

### Typography

- Font Family: Nunito (Google Fonts)
- Rounded buttons: `rounded-2xl`

### Key Features

- **Audience toggle** - Top navigation toggle switches the hero and feature list between Members, Institutions, and Community
- **Deep links** - `index.html#members`, `#institutions`, and `#community` open that audience's features. The footer uses these on both pages
- **Coming Soon band** - The yellow section at the bottom of both pages lists the three launch platforms
- **Mobile-first responsive design**

## At Launch

Places that are waiting on a live product:

- **Platform cards** in the `#coming-soon` band (both pages) are plain `<div>`s. Turn them into links to the App Store, Google Play, and the web app
- **Nav** has a "Coming Soon" button where Sign In / Get Started used to be
- **Hero buttons** scroll within the page instead of starting sign-up or booking a demo
- **Removed until there is real content**: member testimonials, the partner credit union logo row, and usage statistics (members served, engagement rate, member savings). The originals are in git history before the rebrand commit
- **Footer** Privacy Policy, Terms of Service, and social icons are still `#` placeholders

## Placeholder Graphics Needed

All photos are stock images from Unsplash.

### index.html

1. **Hero Illustration (Members)**
   - Description: Person using the CentScope app on a phone, surrounded by floating icons (home, car, graduation cap, piggy bank)
   - Dimensions: 600x500px
   - Style: Bright, friendly, matches the blue palette with yellow and lime accents

2. **Hero Illustration (Institutions)**
   - Description: Dashboard mockup showing analytics, member engagement graphs
   - Dimensions: 600x500px
   - Style: Professional, data-driven

3. **Hero Illustration (Community)**
   - Description: Community partners working with members
   - Dimensions: 600x500px
   - Style: Sits on the yellow → lime background, so avoid yellow-heavy imagery

### about.html

1. **Team/Community Photo**
   - Description: Diverse group of coaches, members, credit union staff together
   - Dimensions: 600x450px
   - Style: Warm, inclusive, welcoming

2. **Team Member Headshots**
   - Description: 3 professional photos for team section. Names and bios are placeholders too
   - Dimensions: 200x200px circular

3. **Partnership Illustration**
   - Description: Credit union building with connected dots leading to happy members on devices
   - Dimensions: 500x400px
   - Style: Professional illustration in the brand palette

## Running Locally

Simply open the HTML files in a browser - no build process required. Links between pages are relative, so this works from `file://` as well as from a server.

```bash
# Using Python
python -m http.server 8000

# Using Node.js
npx serve .

# Or just open directly
open index.html
```

## Technologies

- Tailwind CSS (via CDN)
- Google Fonts (Nunito)
- Vanilla JavaScript (for toggle functionality)
- No build process required
