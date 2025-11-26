# TPV Author Influence Database - GitHub Pages Deployment

This directory contains everything needed to deploy the TPV Author Influence Database to GitHub Pages.

## 📁 Files

- **`index.html`** - Interactive web interface with search, sort, and filtering
- **`author_metrics.json`** - Complete author data (used by index.html)
- **`author_metrics.csv`** - Spreadsheet-friendly export

## 🚀 Quick Deploy to GitHub Pages

### Option 1: New Repository

1. **Create a new GitHub repository** (e.g., `tpv-author-database`)

2. **Upload these files** to the repository:
   ```
   /
   ├── index.html
   ├── author_metrics.json
   └── README.md (optional)
   ```

3. **Enable GitHub Pages:**
   - Go to repository Settings
   - Scroll to "Pages" section
   - Source: Deploy from main branch
   - Directory: `/` (root)
   - Click Save

4. **Access your site:**
   - `https://[your-username].github.io/tpv-author-database/`

### Option 2: Existing Repository (Subfolder)

If you want to add this to an existing repository:

1. **Create a subdirectory** (e.g., `/tpv-database/`)
2. **Upload the files** to that directory
3. **Enable GitHub Pages** (same as above)
4. **Access via:** `https://[your-username].github.io/[repo-name]/tpv-database/`

### Option 3: Using Git Command Line

```bash
# Create new repo on GitHub first, then:
cd outputs/tpv
git init
git add index.html author_metrics.json README.md
git commit -m "Initial commit: TPV Author Influence Database"
git branch -M main
git remote add origin https://github.com/[your-username]/tpv-author-database.git
git push -u origin main
```

Then enable GitHub Pages in repository settings.

## 🎨 Features

The web interface includes:

### Interactive Features
- **Search**: Real-time search by author name, affiliation
- **Sort**: Click column headers to sort
- **Filter**: Dropdown menus for quick filtering
- **Pagination**: View 25, 50, 100, or all authors
- **Export**: Download current view as CSV

### Metrics Displayed
- **h-index**: Papers with h+ citations (color-coded)
- **i10-index**: Papers with 10+ citations
- **Total Publications**: All papers by author
- **Total Citations**: Cumulative citations
- **Average Citations**: Per paper
- **Journal Papers**: Papers in TPV
- **Career Span**: Years active

### Dashboard Stats
- Total Authors (1,891)
- Total Publications (53,025)
- Average h-index (8.47)
- Total Citations (1.35M)

## 📊 Data Structure

The `author_metrics.json` file structure:

```json
{
  "metadata": {
    "generated_at": "2025-11-26T...",
    "total_authors": 1891,
    "database": "tpv_database"
  },
  "authors": [
    {
      "author_id": "...",
      "author_name": "Kruglanski, A.W.",
      "h_index": 118,
      "total_publications": 852,
      "total_citations": 65408,
      ...
    }
  ]
}
```

## 🔄 Updating Data

To update the data:

1. **Re-run the analysis script:**
   ```bash
   python scripts/analyze_author_influence.py --db-name TPV_DB_NAME --output-dir outputs/tpv
   ```

2. **Commit and push the updated JSON:**
   ```bash
   git add author_metrics.json
   git commit -m "Update author metrics - [date]"
   git push
   ```

GitHub Pages will automatically rebuild (may take a few minutes).

## 🎨 Customization

### Change Colors

Edit the CSS in `index.html`:

```css
/* Main gradient */
background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);

/* Stat cards gradient */
.stat-card {
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
}
```

### Change Title

Edit line ~45 in `index.html`:

```html
<h1>Terrorism and Political Violence</h1>
<p class="subtitle">Author Influence Database</p>
```

### Add Custom Logo

Insert before the `<h1>` tag:

```html
<img src="logo.png" alt="Journal Logo" style="max-width: 200px;">
```

## 🔗 Custom Domain

To use a custom domain (e.g., `authors.yourjournal.com`):

1. **Add CNAME file** to repository:
   ```
   authors.yourjournal.com
   ```

2. **Configure DNS** with your domain provider:
   - Add CNAME record pointing to: `[your-username].github.io`

3. **Update GitHub Pages settings** with custom domain

## 📱 Mobile Responsive

The interface is fully responsive and works on:
- Desktop browsers
- Tablets
- Mobile phones

## 🚦 Performance

- **Load Time**: < 1 second (data is ~3MB compressed)
- **Search**: Real-time (no lag)
- **Works Offline**: Once loaded, fully functional offline

## 🔒 Privacy

All data is:
- Publicly accessible (GitHub Pages is public)
- Static (no server-side processing)
- No tracking/analytics (unless you add it)

## 💡 Pro Tips

1. **Add Google Analytics** (if desired):
   ```html
   <!-- Add before </head> -->
   <script async src="https://www.googletagmanager.com/gtag/js?id=YOUR-ID"></script>
   ```

2. **Add Favicon**:
   ```html
   <link rel="icon" href="favicon.ico">
   ```

3. **Social Media Preview**:
   ```html
   <meta property="og:title" content="TPV Author Influence Database">
   <meta property="og:description" content="1,891 authors, 53,025 publications">
   <meta property="og:image" content="preview.png">
   ```

## 🐛 Troubleshooting

**Issue**: 404 Error
- **Fix**: Check repository settings > Pages > ensure correct branch/folder

**Issue**: Data not loading
- **Fix**: Check browser console (F12) for errors. Ensure `author_metrics.json` is in same directory

**Issue**: Slow performance
- **Fix**: Reduce `perPage` default or enable pagination by default

## 📧 Support

For issues with:
- **Database**: Check main project README
- **GitHub Pages**: See [GitHub Pages Docs](https://docs.github.com/en/pages)
- **Web Interface**: Check browser console for errors

## 📄 License

Same as main project.
