# ⚡ SA Electricity News

**Automated daily aggregation of South African electricity and energy news.**

Covers Eskom, NERSA, load shedding, tariffs, renewable energy, grid infrastructure, and more — updated every evening via GitHub Actions.

---

## How It Works

1. **Python scraper** fetches articles from 10+ South African news RSS feeds and Google News
2. **Keyword filtering** ensures only electricity/energy-related articles are included
3. **Deduplication** removes duplicate articles across sources
4. **Static site builder** generates a clean HTML page with category filtering and search
5. **GitHub Actions** runs the scraper daily at 18:00 SAST and deploys to GitHub Pages

## Quick Setup (5 minutes)

### 1. Create a GitHub Repository

```bash
# Clone or download this project
git init sa-electricity-news
cd sa-electricity-news

# Copy all project files into this directory, then:
git add .
git commit -m "Initial commit: SA Electricity News aggregator"
```

### 2. Push to GitHub

```bash
# Create a new repository on GitHub (e.g., sa-electricity-news), then:
git remote add origin https://github.com/YOUR_USERNAME/sa-electricity-news.git
git branch -M main
git push -u origin main
```

### 3. Enable GitHub Pages

1. Go to your repository on GitHub
2. Navigate to **Settings** → **Pages**
3. Under **Source**, select **GitHub Actions**
4. That's it! The workflow will handle deployment

### 4. Run the First Scrape

1. Go to the **Actions** tab in your repository
2. Click on **"Scrape SA Electricity News"** workflow
3. Click **"Run workflow"** → **"Run workflow"** (green button)
4. Wait a few minutes for it to complete
5. Your site will be live at `https://YOUR_USERNAME.github.io/sa-electricity-news/`

## Running Locally

```bash
# Install dependencies
pip install -r requirements.txt

# Run the scraper
python run_scraper.py

# Open index.html in your browser
open index.html  # macOS
xdg-open index.html  # Linux
```

## Project Structure

```
sa-electricity-news/
├── .github/workflows/
│   └── scrape-news.yml      # GitHub Actions workflow (daily cron)
├── scraper/
│   ├── __init__.py
│   ├── config.py             # Search queries, RSS feeds, keywords
│   ├── fetcher.py            # News scraping and filtering logic
│   ├── builder.py            # Static site generator
│   └── main.py               # Main scraper pipeline
├── static/
│   ├── css/style.css         # Site stylesheet
│   └── js/app.js             # Client-side filtering & search
├── templates/
│   └── index.html            # Jinja2 template for the site
├── data/
│   └── articles.json         # Scraped articles (auto-generated)
├── index.html                # Built site (auto-generated)
├── requirements.txt          # Python dependencies
├── run_scraper.py            # Entry point script
└── README.md
```

## Configuration

Edit `scraper/config.py` to:

- **Add/remove RSS feeds** — update `RSS_FEEDS` dict
- **Change search queries** — update `SEARCH_QUERIES` list
- **Adjust keyword filters** — update `FILTER_KEYWORDS` list
- **Change article age limit** — update `MAX_ARTICLE_AGE_DAYS` (default: 3 days)
- **Change max articles** — update `MAX_ARTICLES` (default: 50)

## Adding a Custom Domain

1. Purchase a domain (e.g., from Namecheap, GoDaddy, etc.)
2. Add a `CNAME` file to the repo root containing your domain:
   ```
   saelectricitynews.co.za
   ```
3. Configure DNS: add a CNAME record pointing to `YOUR_USERNAME.github.io`
4. In GitHub repo Settings → Pages, enter your custom domain

## News Sources

The scraper pulls from these South African sources:

| Source | Type |
|--------|------|
| Eyewitness News | RSS Feed |
| News24 | RSS Feed |
| Daily Maverick | RSS Feed |
| Engineering News | RSS Feed |
| ESI Africa | RSS Feed |
| MyBroadband | RSS Feed |
| BusinessTech | RSS Feed |
| TimesLive | RSS Feed |
| Moneyweb | RSS Feed |
| Google News ZA | Search RSS |

## Article Categories

Articles are automatically categorized into:

- **Load Shedding** — Outages, stages, schedules
- **Tariffs & Pricing** — Rate increases, NERSA decisions
- **Renewable Energy** — Solar, wind, IPPs, battery storage
- **Eskom Operations** — Power stations, maintenance, capacity
- **Regulation & Policy** — NERSA, DMRE, legislation
- **Grid & Infrastructure** — Transmission, distribution, theft
- **Energy Transition** — JET, decarbonization, climate
- **General** — Other energy-related news

## License

This project aggregates publicly available news. All articles link to their original sources.
