# XC Skies Integration Guide

## Overview

This guide provides step-by-step instructions for adding XC Skies forecast integration to the Bay Area Soaring dashboard. The XC Skies tabs will provide quick access to paragliding-specific forecasts for Ed R. Levin Park and Mussel Rock Park.

**Time Required:** 10-15 minutes  
**Difficulty:** Beginner  
**Prerequisites:** Git, text editor (VS Code recommended)

---

## Background

XC Skies (https://www.xcskies.com) provides specialized soaring forecasts with thermal predictions and cross-country flying conditions. However, they don't offer a public API or embeddable widgets. This integration uses deep-link buttons that open XC Skies map views with site-specific coordinates.

---

## Step 1: Clone the Repository

Open Terminal and run:

```bash
git clone https://github.com/flybayarea/bay-area-soaring.git
cd bay-area-soaring
```

---

## Step 2: Open index.html

Open `index.html` in your preferred text editor:

```bash
code index.html    # VS Code
# OR
open -a "Sublime Text" index.html
# OR any other editor
```

**Note:** The file is minified (single line, ~28KB). Use your editor's "Format Document" feature for easier editing.

---

## Step 3: Add XC Skies Tab Buttons

### For Ed R. Levin Park

**Find this line** (use Cmd+F / Ctrl+F):
```html
<button class="tb" onclick="sw('lev','nws',this)">NWS Forecast</button></div>
```

**Replace with:**
```html
<button class="tb" onclick="sw('lev','nws',this)">NWS Forecast</button><button class="tb" onclick="sw('lev','xc',this)">XC Skies</button></div>
```

### For Mussel Rock Park

**Find this line:**
```html
<button class="tb" onclick="sw('mus','nws',this)">NWS Forecast</button></div>
```

**Replace with:**
```html
<button class="tb" onclick="sw('mus','nws',this)">NWS Forecast</button><button class="tb" onclick="sw('mus','xc',this)">XC Skies</button></div>
```

---

## Step 4: Add XC Skies Tab Content

### For Ed R. Levin Park

**Find this block:**
```html
<div id="lev-nws" class="tc"><div id="lev-nws-wrap" class="nws-wrap">Loading NWS data...</div></div>
```

**Add immediately after it:**
```html
<div id="lev-xc" class="tc"><div class="desc"><strong>XC Skies Soaring Forecast</strong> provides specialized paragliding forecasts with thermal predictions, wind analysis, and cross-country flying conditions.</div><div class="nws-link-bar"><a href="https://www.xcskies.com/map#lat=37.4619&lon=-121.861&zoom=11" target="_blank" class="nws-link">🗺️ Open XC Skies Map</a><a href="https://www.xcskies.com" target="_blank" class="nws-link">📊 XC Skies Home</a></div><div style="margin-top:16px;padding:12px;background:var(--bg);border:1px solid var(--border);border-radius:8px;font-size:12px;color:var(--muted)">Note: XC Skies requires login for full forecast features. Click the map link above to view interactive forecasts for Ed R. Levin Park.</div></div>
```

### For Mussel Rock Park

**Find this block:**
```html
<div id="mus-nws" class="tc"><div id="mus-nws-wrap" class="nws-wrap">Loading NWS data...</div></div>
```

**Add immediately after it:**
```html
<div id="mus-xc" class="tc"><div class="desc"><strong>XC Skies Soaring Forecast</strong> provides specialized paragliding forecasts with thermal predictions, wind analysis, and cross-country flying conditions.</div><div class="nws-link-bar"><a href="https://www.xcskies.com/map#lat=37.6740&lon=-122.4887&zoom=11" target="_blank" class="nws-link">🗺️ Open XC Skies Map</a><a href="https://www.xcskies.com" target="_blank" class="nws-link">📊 XC Skies Home</a></div><div style="margin-top:16px;padding:12px;background:var(--bg);border:1px solid var(--border);border-radius:8px;font-size:12px;color:var(--muted)">Note: XC Skies requires login for full forecast features. Click the map link above to view interactive forecasts for Mussel Rock Park.</div></div>
```

---

## Step 5: Save and Test Locally

1. Save `index.html`
2. Open it in your browser:
   ```bash
   open index.html    # macOS
   # OR
   start index.html   # Windows
   ```
3. Verify both parks now have 5 tabs: Today, Tomorrow, 6-Day Outlook, NWS Forecast, **XC Skies**
4. Click the XC Skies tabs and test the map links

---

## Step 6: Commit and Push

```bash
git add index.html
git commit -m "Add XC Skies tab integration for both parks"
git push origin main
```

---

## Step 7: Verify Live Deployment

1. Wait 1-2 minutes for GitHub Pages to deploy
2. Visit: https://flybayarea.github.io/bay-area-soaring/
3. Verify XC Skies tabs are working on both park cards

---

## Coordinates Reference

- **Ed R. Levin Park:** 37.4619°N, 121.861°W
- **Mussel Rock Park:** 37.6740°N, 122.4887°W

---

## Troubleshooting

### XC Skies tabs not appearing
- Clear browser cache (Cmd+Shift+R / Ctrl+Shift+F5)
- Check GitHub Actions for deployment errors
- Verify the HTML syntax is correct (no missing quotes or brackets)

### Links not working
- Ensure `target="_blank"` is included so links open in new tabs
- Test the XC Skies URLs directly in a browser

### Tab switching not working
- Verify the `onclick="sw('lev','xc',this)"` matches the div ID `id="lev-xc"`
- Check browser console for JavaScript errors

---

## What Was Added

✅ XC Skies tab buttons for Ed R. Levin Park and Mussel Rock Park  
✅ XC Skies content sections with forecast descriptions  
✅ Deep-link buttons to XC Skies interactive maps  
✅ Site-specific coordinates in map URLs  
✅ User notes about XC Skies login requirements  

---

## Alternative: Using Find & Replace

If you prefer to use find-and-replace in your editor:

**Find:** `onclick="sw('lev','nws',this)">NWS Forecast</button></div>`  
**Replace with:** `onclick="sw('lev','nws',this)">NWS Forecast</button><button class="tb" onclick="sw('lev','xc',this)">XC Skies</button></div>`

Repeat for Mussel Rock (`'mus'` instead of `'lev'`).

Then do the same for the content divs using the blocks in Step 4.

---

## Support

For issues or questions:
- GitHub Issues: https://github.com/flybayarea/bay-area-soaring/issues
- XC Skies Support: https://www.xcskies.com/docs

---

## License

This integration guide is part of the Bay Area Soaring project.

---

**Last Updated:** May 29, 2026  
**Author:** Bay Area Soaring Contributors
