# OHGOD Philosophy

**One Hobbyist GPU, One Day**: A framework proposing that powerful AI can be trained on consumer-grade hardware in 24 hours.

Website: [ohgodmodels.xyz](https://ohgodmodels.xyz)

## Prerequisites

- **Ruby** (version 2.7 or higher)
- **Bundler** (Ruby gem manager)

### macOS

```bash
# Install Ruby via Homebrew (recommended)
brew install ruby

# Add to your shell profile (~/.zshrc or ~/.bashrc)
export PATH="/opt/homebrew/opt/ruby/bin:$PATH"

# Install Bundler
gem install bundler
```

### Ubuntu/Debian

```bash
sudo apt update
sudo apt install ruby-full build-essential zlib1g-dev

# Install Bundler
gem install bundler
```

### Windows

Use [RubyInstaller](https://rubyinstaller.org/) with DevKit.

## Local Development

### 1. Clone the repository

```bash
git clone https://github.com/ohgodmodels/ohgodmodels.github.io.git
cd ohgodmodels.github.io
```

### 2. Install dependencies

```bash
bundle install
```

### 3. Run the development server

```bash
bundle exec jekyll serve
```

The site will be available at: **http://localhost:4000**

### Live reload (auto-refresh on changes)

```bash
bundle exec jekyll serve --livereload
```

### Build only (no server)

```bash
bundle exec jekyll build
```

Output goes to `_site/` directory.

## Project Structure

```
.
├── _config.yml              # Jekyll configuration
├── _includes/
│   ├── hero.html            # Hero section
│   ├── call-to-action.html  # CTA section
│   ├── observations/
│   │   ├── observations.html       # Card grid (Part I)
│   │   ├── observation-card.html   # Flip card component
│   │   ├── observation-detail.html # Detail page template
│   │   └── observation-1.html ...  # Individual observation data
│   └── experiments/
│       └── experiments.html        # Experiments section (Part II)
├── _layouts/
│   └── default.html         # Master layout
├── index.html               # Main page
├── Gemfile                  # Ruby dependencies
└── CLAUDE.md                # HN story selection guidelines
```

## Making Changes

### Updating an observation card

Edit the card parameters in `_includes/observations/observations.html`:

```liquid
{% include observations/observation-card.html
    number="1"
    title="industry.close()"
    icon="building"
    color="red"
    description="Your description here"
    stat="$5B"
    stat_label="Stat explanation"
    story1_url="https://news.ycombinator.com/item?id=XXXXX"
    story1_title="Story Title"
    story1_summary="Brief summary"
    ... (4 stories total)
%}
```

### Updating observation detail pages

Edit `_includes/observations/observation-N.html` files.

### Available colors

`red`, `amber`, `cyan`, `purple`, `pink`, `orange`

### Available icons

`building`, `lightning`, `eye`, `lock`, `brain`, `cube`

## Deployment

The site automatically deploys to GitHub Pages when pushing to `main` branch.

Manual build for other hosting:

```bash
JEKYLL_ENV=production bundle exec jekyll build
# Upload contents of _site/ to your host
```

## Troubleshooting

### Bundle install fails

```bash
# Update bundler
gem install bundler

# Clear cache and retry
rm -rf vendor/
bundle install
```

### Permission errors on macOS

```bash
# Install gems to user directory
bundle config set --local path 'vendor/bundle'
bundle install
```

### Port 4000 already in use

```bash
bundle exec jekyll serve --port 4001
```

## License

MIT
