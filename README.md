# Portfolio Website Template

A free, modern portfolio website template for developers, consultants, and software companies. Built with clean HTML, CSS, and vanilla JavaScript — no build tools required.

**[Live Site: okeke.us](https://okeke.us)**

---

## Screenshots

![Homepage Hero](screenshots/homepage-hero.png)

![Apps Page](screenshots/apps-page.png)

![CTA Section](screenshots/cta-footer.png)

---

## Features

### Design
- Clean, professional design with Inter font
- Subtle snowfall animation (respects `prefers-reduced-motion`)
- Fully responsive with mobile hamburger menu
- Two-column hero layout with image
- Independent expandable sections across all pages
- Favicon support for browser tabs and mobile home screens

### Pages Included
| Page | Description |
|------|-------------|
| **Homepage** | Hero section with 4 mission cards (Enhance Efficiency, Boost ROI, Create Assets, Mobilize AI), platform integration ticker, and quick actions |
| **Services** | 4 service categories (Automation, Platform Integration, Custom Software Development, AI Mobilization) with collapsible nested service items |
| **Research** | 6 technology focus areas (AI & ML, Cloud Architecture, Swift & Apple Platforms, DevOps, Data & Analytics, Security) with expandable details |
| **Blog** | Article listing with featured posts and quick navigation |
| **Apps** | 2 app categories (Business Apps, Consumer Apps) plus AI Platform section with 8+ apps showcased |
| **About** | 3 collapsible sections (Our Mission, Proven Results, Our Principles) with nested expandable principle items |
| **Contact** | Contact form with spam protection, hours, phone, and email |

### SEO & AI Optimized
- Schema.org structured data (ProfessionalService, WebSite)
- Open Graph & Twitter Card meta tags
- XML sitemap with priority levels
- AI crawler friendly (`robots.txt` allows GPTBot, Claude, Perplexity, etc.)
- Semantic HTML with ARIA labels

### Interactive Elements
- **Independent expandable cards**: Click any card to expand/collapse without affecting others
- **No stretching**: Cards maintain their height when collapsed, even when other cards expand
- **Smooth animations**: CSS transitions for expand/collapse with max-height and opacity
- **Nested expandables**: Services, Research, and About pages support nested collapsible items

### Contact Form
- Powered by [Formspree](https://formspree.io) (free tier: 50 submissions/month)
- Honeypot spam protection (no annoying CAPTCHAs)
- Contact methods displayed (hours, phone, email)
- Optional company field
- Mobile-responsive layout

---

## Quick Start

### 1. Clone the repo
```bash
git clone https://github.com/okekedev/portfoliotemplate.git
cd portfoliotemplate
```

### 2. Run locally
```bash
# Python
python -m http.server 8000

# Or Node.js
npx serve .

# Visit http://localhost:8000
```

### 3. Customize
- Update company name, colors, and content
- Replace images in `/images/`
- Replace logo in `/images/logo.png` (used for favicon and nav)
- Set up your Formspree form (see below)

---

## Customization

### Colors
Edit `styles.css`:
```css
:root {
    --color-primary: #2563eb;    /* Blue accent */
    --color-text: #1a1a1a;       /* Dark text */
    --color-bg-alt: #f8f9fa;     /* Light sections */
}
```

### Contact Form Setup
1. Create a free account at [formspree.io](https://formspree.io)
2. Create a new form
3. Copy your form ID
4. Replace in `contact/index.html`:
```html
<form action="https://formspree.io/f/YOUR_FORM_ID" method="POST">
```

### Snowfall Animation
In each HTML file's `<script>` section:
```javascript
// Adjust opacity (0.15-0.35 = subtle, increase for more visible)
opacity: Math.random() * 0.2 + 0.15

// Adjust particle count
const maxSnowflakes = 100;
```

### Favicon Customization
The template uses `/images/logo.png` for the favicon. To customize:
1. Replace `/images/logo.png` with your logo (recommended: 512x512px PNG)
2. For optimal quality, create dedicated favicon files at various sizes (16x16, 32x32, 180x180)
3. Update the favicon links in all HTML files

### Adding Your Apps
Update the apps section with your own projects. App icons can be loaded from Apple's CDN:
```bash
# Get icon URL for any App Store app
curl "https://itunes.apple.com/lookup?id=YOUR_APP_ID" | jq '.results[0].artworkUrl512'
```

### Expandable Sections
All expandable sections use `data-expanded` attributes and JavaScript event listeners. Each card expands/collapses independently. The CSS uses:
- `align-items: start` on grid containers to prevent card stretching
- `max-height` and `opacity` transitions for smooth animations
- Unique event listeners per card (no accordion behavior)

---

## Deployment

### Azure Static Web Apps (Recommended)
```bash
# Install Azure CLI if needed
# brew install azure-cli

# Login
az login

# Create resource group
az group create --name website-rg --location "Central US"

# Create static web app (uses your GitHub token)
GH_TOKEN=$(gh auth token) && az staticwebapp create \
  --name your-site-name \
  --resource-group website-rg \
  --source https://github.com/YOUR_USERNAME/portfoliotemplate \
  --branch main \
  --app-location "/" \
  --output-location "/" \
  --token "$GH_TOKEN"
```

Auto-deploys on every push to `main`.

### Other Platforms
Works with any static hosting:
- **Netlify**: Drag & drop or connect GitHub
- **Vercel**: Import from GitHub
- **GitHub Pages**: Enable in repo settings
- **Cloudflare Pages**: Connect GitHub repo

---

## Project Structure

```
portfoliotemplate/
├── index.html              # Homepage with mission cards
├── styles.css              # Global styles
├── robots.txt              # SEO (allows AI crawlers)
├── sitemap.xml             # XML sitemap
├── staticwebapp.config.json # Azure config
│
├── services/               # Services page
│   ├── index.html          # 4 service categories
│   └── services.css        # Service-specific styles
├── research/               # Research/tech page
│   ├── index.html          # 6 focus areas
│   └── research.css        # Research-specific styles
├── blog/                   # Blog listing
│   ├── index.html          # Article listing
│   └── marketing-attribution/  # Individual blog posts
├── apps/                   # Apps portfolio
│   ├── index.html          # Business & consumer apps
│   └── apps.css            # Apps-specific styles
├── about/                  # About page
│   ├── index.html          # Mission, results, principles
│   └── about.css           # About-specific styles
├── contact/                # Contact page with form
│   ├── index.html          # Contact form & info
│   └── contact.css         # Contact-specific styles
├── images/                 # Site images
│   └── logo.png            # Logo (used for nav & favicon)
└── screenshots/            # README screenshots
```

---

## Credits

This template was created for [Okeke LLC](https://okeke.us), a software development and consulting company. We built it for our own site and decided to share it as a free template for the community.

**Built with:**
- [Inter Font](https://fonts.google.com/specimen/Inter)
- [Formspree](https://formspree.io) for contact forms
- [Azure Static Web Apps](https://azure.microsoft.com/en-us/products/app-service/static) for hosting

---

## License

This project is available under a Research and Educational Use License. See [LICENSE](LICENSE) for details.

**Summary:**
- Free for personal, educational, and research use
- Commercial use requires permission
- Attribution appreciated but not required

For commercial licensing, contact: contact@okeke.us
