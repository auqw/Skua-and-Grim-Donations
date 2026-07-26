# 🐙 Skua & Grim Donations

An interactive donations page supporting the developers behind **Skua**, **Grim**, **VibeSkua**, and **AQI Beyond**. Built with vanilla HTML/CSS/JS, hosted on GitHub Pages.

**Live site:** https://auqw.github.io/Skua-and-Grim-Donations/

## What this is

A single-page site (`index.html`) listing current and past contributors across four client branches, with quick-copy payment links and status badges (Active / On Hiatus / No Longer Active).

**Groups currently tracked:**
- 💜 **SKUA** — the original client
- 🌙 **GRIM** — Grim client versions
- 🌈 **VibeSkua** — the VibeSkua branch of 1.4.3.0
- ✨ **AQI Beyond** — the AQInfinity client

Visitors can filter by group (`SKUA`, `GRIM`, `VibeSkua`, `AQI Beyond`), by `Active` only, or view `All`.

## 🎨 Adding or Updating a Donor

All donor data lives in the `donors` object inside `index.html` (in the `<script>` block near the bottom).

Each group is a key in `donors` (`skua`, `grim`, `vibeskua`, `aqibeyond`), containing an array of donor objects:

```javascript
{
    name: 'Your Name',
    role: 'Your Role / Contribution',
    avatar: 'YN',   // 2-4 char initials, OR a full image URL (e.g. 'https://i.imgur.com/xxxx.png')
    status: 'active',   // 'active' | 'hiatus' | 'inactive'
    payments: [
        { type: 'Ko-fi', value: 'https://ko-fi.com/yourname' },
        { type: 'PayPal', value: 'https://paypal.me/yourname' },
        { type: 'ETH', value: '0xYourEthereumAddress' }
    ]
}
```

**Status meanings:**
- `active` — shown at the top of the group with a green ✓ badge
- `hiatus` — shown under "Past Contributors" with an orange ⏱ badge ("On Hiatus")
- `inactive` — shown under "Past Contributors" with a red ✕ badge ("No longer active")

### Adding a brand-new group (not just a new donor)

If you ever need a fifth group beyond SKUA/GRIM/VibeSkua/AQI Beyond, three things all need to be added together, or the group silently won't render:

1. A new key + donor array under `donors` in the script.
2. A matching HTML `<div class="section">` block with `id="<key>-active"`, `id="<key>-inactive"`, and the corresponding `-active-grid` / `-inactive-grid` container divs (copy an existing section as a template).
3. A filter button: `<button class="filter-btn" data-filter="<key>">Label</button>`.

The render logic (`renderDonors` / `renderGroup`) auto-detects any group name that has matching HTML IDs, so no JS changes are needed beyond that — just make sure the `<key>` used in `donors` matches the ID prefixes exactly.

## 🎨 Customization

**Theme colors** — CSS variables near the top of `index.html`:
```css
:root {
    --primary: #8b5cf6;
    --primary-dark: #7c3aed;
    --bg-dark: #0f172a;
    --bg-card: #1e1b4b;
    --border-color: #4c1d95;
    --text-primary: #f8fafc;
    --text-secondary: #cbd5e1;
    --status-active: #10b981;
    --status-inactive: #ef4444;
    --status-hiatus: #f59e0b;
}
```

**Payment method icons** — add new types in `getPaymentIcon()`:
```javascript
function getPaymentIcon(type) {
    const icons = {
        'PayPal': '🅿️',
        'Ko-fi': '☕',
        'ETH': '⟠',
        'Your Method': '🎯'  // add here
    };
    return icons[type] || '💳';
}
```

**Grid column width** — `.donors-grid { grid-template-columns: repeat(auto-fill, minmax(350px, 1fr)); }`

## 🎁 Donor Perks

After donating, contact the developer you supported to receive the **Donor role** in Discord. Perks include:
- Custom role color (provide a hex code)
- Custom role name
- Custom role icon (emoji or a strictly SFW image)

## 📝 Deploying Changes

This repo deploys via **GitHub Pages from the `master` branch, root folder**. Any push to `master` that touches `index.html` goes live within seconds — no build step required.

```bash
git add index.html
git commit -m "Update donor list"
git push
```

If changes don't appear immediately, hard-refresh your browser (Ctrl+Shift+R / Cmd+Shift+R) — GitHub Pages updates fast, but browsers cache aggressively.

## ✨ Features

- ✅ Copy-to-clipboard for payment links
- ✅ Filter by group or by Active status
- ✅ Responsive layout (mobile/tablet/desktop)
- ✅ Active supporters surfaced above past contributors
- ✅ No build process — plain HTML/CSS/JS, no dependencies

---

**Made with 💜 for Skua & Grim**