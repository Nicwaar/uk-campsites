# UK Campsite Interactive Map - Complete Wix Integration Guide

## 📦 What You've Received

You now have 3 files:

1. **uk-campsite-map.html** - Main interactive map page
2. **scotland-campsites-page.html** - Template for regional campsite listing pages
3. **campsites-data.json** - Sample data structure with campsite information

---

## 🎯 Implementation Options for Wix Studio (All FREE)

### **Option 1: Host Files Externally (Recommended)**

This is the easiest method and gives you full control.

#### Step 1: Choose a Free Hosting Platform

**Best Options:**
- **GitHub Pages** (Easiest, most reliable)
- **Netlify** (Great for beginners)
- **Cloudflare Pages** (Fast and free)
- **Vercel** (Developer-friendly)

#### Step 2: Host Your Files

**Using GitHub Pages (Recommended):**

1. Create a free GitHub account at github.com
2. Create a new repository called "uk-campsites"
3. Upload your HTML files to the repository
4. Go to Settings → Pages
5. Enable GitHub Pages (select main branch)
6. Your files will be available at: `https://yourusername.github.io/uk-campsites/uk-campsite-map.html`

**Using Netlify:**

1. Sign up at netlify.com (free)
2. Drag and drop your files into Netlify's drop zone
3. Get instant URL like: `https://your-site-name.netlify.app/uk-campsite-map.html`

#### Step 3: Add to Wix Studio

1. Open Wix Studio editor
2. Click **"Add Elements"** (+) on left side
3. Select **"Embed Code" → "Custom Element"**
4. Drag the element onto your page
5. Click **"Choose Source"** → **"Website Address (URL)"**
6. Paste your hosted file URL (e.g., `https://yourusername.github.io/uk-campsites/uk-campsite-map.html`)
7. Set size: Width 100%, Height 800-1000px
8. Click "Update"

---

### **Option 2: Embed Code Directly in Wix**

If you prefer not to use external hosting:

1. In Wix Studio, add **"HTML iframe"** element
2. Click **"Enter Code"**
3. Copy the ENTIRE content of `uk-campsite-map.html`
4. Paste into the code editor
5. Save and preview

**Limitations:**
- Larger file sizes may cause issues
- Updates require re-pasting code
- Less flexible for maintenance

---

## 🗺️ Setting Up Regional Pages in Wix

### Step 1: Create Pages for Each Region

In Wix Studio:

1. Go to **"Pages & Menu"** (left sidebar)
2. Click **"Add Page"**
3. Create pages with these exact names:
   - `/scotland`
   - `/wales`
   - `/north-east`
   - `/north-west`
   - `/yorkshire`
   - `/midlands`
   - `/east-anglia`
   - `/south-west`
   - `/south-east`
   - `/london`
   - `/northern-ireland`

### Step 2: Add Regional Content

For each regional page:

1. **Using External Hosting:**
   - Host the `scotland-campsites-page.html` file
   - Customize it for each region (change region name, load different data)
   - Embed using Custom Element (same as main map)

2. **Using Wix Editor:**
   - Use the template as design inspiration
   - Recreate the layout using Wix elements
   - Connect to Wix Collections (see database section)

---

## 💾 Database Options for Campsite Data

### **Option 1: Wix Collections (Recommended for Wix)**

**Advantages:**
- Built into Wix
- No external dependencies
- Easy updates via CMS
- Good for dynamic content

**Setup:**

1. Go to **CMS** in Wix Studio
2. Create new collection called **"Campsites"**
3. Add these fields:

| Field Name | Type | Notes |
|------------|------|-------|
| name | Text | Campsite name |
| region | Text | scotland, wales, etc. |
| address | Text | Full address |
| what3words | Text | ///three.word.address |
| url | URL | Website link |
| rating | Number | 0-5 rating |
| status | Text | visited, favorite, wishlist |
| ehu | Boolean | Has electric hookup |
| openAllYear | Boolean | Open year-round |
| openMonths | Text | e.g., "March - October" |
| onsite | Text | Comma-separated facilities |
| nearby | Text | Comma-separated activities |
| comments | Rich Text | User comments |
| latitude | Number | Decimal coordinates |
| longitude | Number | Decimal coordinates |
| pitchTypes | Text | Types of pitches available |
| petFriendly | Boolean | Allows pets |
| priceRange | Text | £, ££, or £££ |

4. Import data from `campsites-data.json`
5. Enable dataset connections in your pages

---

### **Option 2: Google Sheets API (Free & Easy)**

**Advantages:**
- Easy to update (like Excel)
- Shareable with family
- Free forever
- Simple API

**Setup:**

1. Create a Google Sheet with your campsite data
2. File → Share → Publish to Web → CSV
3. Use the public URL in your JavaScript
4. Parse CSV data using JavaScript

**JavaScript Example:**

```javascript
async function loadCampsites() {
    const url = 'YOUR_GOOGLE_SHEETS_CSV_URL';
    const response = await fetch(url);
    const csvText = await response.text();
    const data = parseCSV(csvText);
    displayCampsites(data);
}
```

---

### **Option 3: JSON File (Simplest)**

**Advantages:**
- No API needed
- Works offline
- Complete control

**Setup:**

1. Host `campsites-data.json` with your HTML files
2. Load data using JavaScript:

```javascript
async function loadCampsites() {
    const response = await fetch('campsites-data.json');
    const data = await response.json();
    return data;
}
```

---

### **Option 4: Airtable (User-Friendly)**

**Advantages:**
- Beautiful interface
- Free tier (1,200 records)
- Easy API integration
- Mobile app for updates

**Setup:**

1. Sign up at airtable.com
2. Create a base from the template structure
3. Get your API key
4. Use Airtable's JavaScript library

---

## 🎨 Customization Guide

### Changing Colors

Edit the CSS variables in the `<style>` section:

```css
:root {
    --forest-dark: #1a3e2f;    /* Dark green */
    --forest-mid: #2d5f4d;     /* Mid green */
    --moss: #7da87b;           /* Light green */
    --sage: #b8c5b0;           /* Sage green */
    --cream: #f5f3ed;          /* Background */
    --earth: #8b6f47;          /* Brown/earth */
    --sunset: #d97652;         /* Orange */
    --water: #6b9fb5;          /* Blue */
}
```

### Changing Fonts

Replace the Google Fonts import:

```html
<link href="https://fonts.googleapis.com/css2?family=YourFont:wght@400;600;700&display=swap" rel="stylesheet">
```

Then update:
```css
body {
    font-family: 'YourFont', sans-serif;
}
```

### Adding More Regions

Edit the SVG map section in `uk-campsite-map.html`:

```html
<path class="region" id="your-region-name"
      d="M coordinates here" />
<text class="region-label" x="X" y="Y">Region Name</text>
```

---

## 🔧 Advanced Features You Can Add

### 1. Real Map Pins

Instead of using the simplified UK map, integrate with:
- **Leaflet.js** (open-source, free)
- **Mapbox** (free tier available)
- **Google Maps API** (requires billing but has free tier)

### 2. Search Functionality

Add a search bar to filter campsites:

```javascript
function searchCampsites(query) {
    const campsites = document.querySelectorAll('.campsite-card');
    campsites.forEach(card => {
        const name = card.querySelector('.campsite-name').textContent.toLowerCase();
        const address = card.querySelector('.info-text').textContent.toLowerCase();
        if (name.includes(query.toLowerCase()) || address.includes(query.toLowerCase())) {
            card.style.display = 'block';
        } else {
            card.style.display = 'none';
        }
    });
}
```

### 3. User Authentication

Allow users to save their own lists:
- Use Wix Members Area (built-in)
- Each user can mark visited/favorites
- Data stored per user

### 4. Reviews System

Add user-submitted reviews:
- Create Wix Forms for review submission
- Store in Wix Collections
- Display on campsite cards

---

## 📱 Mobile Optimization

The provided files are already mobile-responsive, but you can enhance:

1. **Larger touch targets** - Make buttons bigger on mobile
2. **Simplified filters** - Collapse into dropdown menu
3. **Swipeable cards** - Add horizontal scrolling for campsites

---

## 🚀 Going Live Checklist

- [ ] All regional pages created in Wix
- [ ] Main map uploaded and embedded
- [ ] Regional templates customized for each area
- [ ] Database/data source connected
- [ ] All links tested (map clicks go to correct pages)
- [ ] Mobile view tested
- [ ] What3words links working
- [ ] External website links verified
- [ ] Filter functionality tested
- [ ] Cross-browser testing (Chrome, Safari, Firefox)

---

## 🆘 Troubleshooting

### Map not clickable in Wix
- Check Custom Element permissions
- Ensure iframe is not blocking interactions
- Try different hosting service

### Regional pages not loading
- Verify page URLs match region IDs exactly
- Check for typos in page names
- Ensure pages are published, not in draft

### Data not displaying
- Check console for errors (F12 in browser)
- Verify data source URL is accessible
- Check data format matches expected structure

### Slow loading
- Optimize images if you add photos
- Minimize JavaScript code
- Use CDN for external libraries

---

## 💡 Tips for Success

1. **Start Simple:** Get the basic map working first, then add features
2. **Test Often:** Preview on different devices regularly
3. **Backup Data:** Keep copies of your campsite data
4. **Document Changes:** Note what you customize for future reference
5. **User Feedback:** Share with friends/family for suggestions

---

## 🔗 Useful Resources

- **Wix Studio Help:** https://support.wix.com/
- **GitHub Pages Guide:** https://pages.github.com/
- **What3Words API:** https://what3words.com/developers
- **Leaflet.js Docs:** https://leafletjs.com/
- **CSS Color Picker:** https://htmlcolorcodes.com/

---

## 📧 Next Steps

1. **Choose your hosting method** (Option 1 recommended)
2. **Upload your files** to chosen hosting
3. **Create regional pages** in Wix
4. **Set up your database** (Wix Collections easiest)
5. **Test the map** clicks and navigation
6. **Add your actual campsite data**
7. **Customize colors and styling** to match your brand
8. **Share with the camping community!** 🏕️

---

## Questions?

If you need help with:
- Converting more regions to pages
- Adding advanced features (real maps, search, user accounts)
- Integrating with specific data sources
- Custom styling or animations
- Performance optimization

Just ask! I can create additional components or provide more specific guidance.

Happy Camping! 🏕️✨
