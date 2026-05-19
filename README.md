# 🐙 Skua & Grim Donations

A beautiful, interactive donations page for Skua & Grim project supporters. Built with vanilla HTML/CSS/JS and hosted on GitHub Pages.

**Live Demo:** Visit your deployed site at `https://your-username.github.io/`

## 🚀 Quick Start

### 1. Setup on GitHub

1. Create a new public repository on [GitHub](https://github.com/new)
   - Name it `your-username.github.io` (for a personal site) or anything else
   - Make it **public**
   - Click "Create repository"

2. Clone the repo and add files:
   ```bash
   git clone https://github.com/your-username/your-repo-name.git
   cd your-repo-name
   # Copy index.html and README.md into this folder
   ```

3. Push to GitHub:
   ```bash
   git add .
   git commit -m "Add donations page"
   git push
   ```

4. Enable GitHub Pages:
   - Go to **Settings** → **Pages**
   - Select **Deploy from a branch**
   - Choose **main** branch, **/root** folder
   - Click **Save**

Your site will be live at `https://your-username.github.io/` in a few seconds!

## 🎨 Customization

### Add or Update Donors

Edit the `donors` object in `index.html` (around line 380):

```javascript
const donors = {
  skua: [
    {
      name: 'Your Name',
      role: 'Your Role',
      avatar: 'YN',  // 2-4 characters shown in circle
      status: 'active',  // 'active', 'inactive', or 'hiatus'
      payments: [
        { type: 'Ko-fi', value: 'https://ko-fi.com/yourname' },
        { type: 'PayPal', value: 'https://paypal.me/yourname' },
        { type: 'ETH', value: '0xYourEthereumAddress' }
      ]
    }
    // Add more donors...
  ],
  grim: [
    // Same structure as skua
  ]
};
```

**Status options:**
- `'active'` - Shows at top with ✓ badge (green)
- `'inactive'` - Shows at bottom with ✕ badge (red) - "No longer active"
- `'hiatus'` - Shows at bottom with ⏱ badge (orange) - "On Hiatus"

**Payment types:** `'Ko-fi'`, `'PayPal'`, `'ETH'`, or create your own

### Change Colors & Theme

All colors are CSS variables at the top of `index.html` (lines 10-18):

```css
:root {
    --primary: #8b5cf6;           /* Main purple */
    --primary-dark: #7c3aed;      /* Darker purple */
    --bg-dark: #0f172a;           /* Dark background */
    --bg-card: #1e1b4b;           /* Card background */
    --border-color: #4c1d95;      /* Border color */
    --text-primary: #f8fafc;      /* Main text */
    --text-secondary: #cbd5e1;    /* Secondary text */
    --status-active: #10b981;     /* Green for active */
    --status-inactive: #ef4444;   /* Red for inactive */
    --status-hiatus: #f59e0b;     /* Orange for hiatus */
}
```

Change any hex code and the whole theme updates instantly!

### Update Text Content

- **Header**: Line ~220 - Change logo emoji and title
- **Subtitle**: Line ~225 - Change "Support the developers & contributors 💜"
- **Section titles**: Lines ~285-290 - Change "SKUA", "GRIM"
- **Perks section**: Lines ~298-320 - Update donor benefits info
- **Footer**: Line ~327 - Change final message

### Add Custom Payment Methods

Need a payment type not in the list? Add it to the `getPaymentIcon()` function (line 387):

```javascript
function getPaymentIcon(type) {
    const icons = {
        'PayPal': '🅿️',
        'Ko-fi': '☕',
        'ETH': '⟠',
        'Your Method': '🎯'  // Add this line
    };
    return icons[type] || '💳';
}
```

Then use it in your donor payment object: `{ type: 'Your Method', value: '...' }`

## ✨ Features

- ✅ **Copy-to-clipboard** - Click any payment link to copy
- ✅ **Smart filtering** - View All, SKUA only, GRIM only, or Active donors
- ✅ **Responsive design** - Works on mobile, tablet, desktop
- ✅ **Smooth animations** - Page load effects and hover interactions
- ✅ **Status organization** - Active supporters at top, past contributors below
- ✅ **Dark mode** - Easy on the eyes with beautiful purple theme
- ✅ **No build process** - Plain HTML/CSS/JS, no dependencies

## 🔧 Advanced Customization

### Change Font

Find the `font-family` on line 44:

```css
font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', 'Roboto', ...
```

Replace with your favorite:
- Modern: `'Inter', 'Helvetica Neue', sans-serif`
- Elegant: `'Georgia', 'Times New Roman', serif`
- Fun: `'Comic Sans MS', cursive` (just kidding 😄)

### Adjust Layout

- **Grid columns**: Line 180 - Change `grid-template-columns: repeat(auto-fill, minmax(350px, 1fr));`
  - Larger cards: `minmax(400px, 1fr)`
  - Smaller cards: `minmax(280px, 1fr)`
  - Fixed 2 columns: `repeat(2, 1fr)`

- **Spacing/padding**: Search for `padding` and `gap` values to adjust

### Add Custom Animations

Modify or add keyframes around line 340:

```css
@keyframes yourAnimation {
    from { /* starting state */ }
    to { /* ending state */ }
}
```

Then apply to elements with `animation: yourAnimation 0.8s ease-out;`

## 📝 Updates & Maintenance

After editing:

```bash
# Make your changes to index.html, then:
git add index.html
git commit -m "Update donor list"
git push
```

Site updates automatically within seconds!

## 🎯 Tips

- **Test locally**: Open `index.html` directly in your browser to preview before pushing
- **Use Chrome DevTools** (F12) to inspect elements and test CSS changes
- **Keep backups** - GitHub has version history, but keep a local copy
- **Mobile friendly** - Always test on phone-sized screens

## 📋 Example: Adding a New Donor

```javascript
{
    name: 'Alice Wonder',
    role: 'Community Manager',
    avatar: 'AW',
    status: 'active',
    payments: [
        { type: 'Ko-fi', value: 'https://ko-fi.com/alicewonder' },
        { type: 'ETH', value: '0x1234567890abcdef...' }
    ]
}
```

## 🤝 Support

Need help? Check:
- GitHub Pages docs: https://pages.github.com/
- CSS reference: https://developer.mozilla.org/en-US/docs/Web/CSS
- HTML elements: https://developer.mozilla.org/en-US/docs/Web/HTML

---

**Made with 💜 for Skua & Grim**

Enjoy your donation page! Don't forget to thank your supporters! 🎉
