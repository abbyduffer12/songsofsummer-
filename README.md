# Songs of the Summer — Jekyll site

A custom, responsive Jekyll starter for publishing a Markdown-based top-10 songs countdown on GitHub Pages. The design uses a warm editorial palette, oversized typography, colorful cover placeholders, and a reusable song layout.

## Project structure

```text
.
├── _config.yml              # Site settings and songs collection
├── _layouts/
│   ├── default.html         # Shared page shell and navigation
│   └── song.html            # Reusable layout for every song review
├── _songs/                  # Your 10 Markdown song pages
├── assets/
│   ├── css/style.css        # Responsive visual theme
│   └── js/main.js           # Optional site interactions
├── index.md                 # Home page and countdown cards
├── 404.md                   # Custom not-found page
├── Gemfile                 # Local Jekyll dependencies
└── README.md
```

## Creating song content

Each file in `_songs/` is a Markdown document. The starter includes `song-01.md` through `song-10.md`; replace the placeholder front matter and review text in each file.

Use this front matter:

```yaml
---
title: "Song title"
performer: "Performer name"
rank: 1
accent: "#ff5e5b"
rating: "4.5 / 5"
stars: "★★★★☆"
---
```

### Front matter fields

- `title`: The song title shown on the home page and review page.
- `performer`: The artist or group name.
- `rank`: A number from 1 to 10. The home page sorts cards by this value.
- `accent`: A hex color used for that song's cover placeholder. Choose a color that works with white text.
- `rating`: The rating text shown beside the stars. You can use a number, fraction, or any short format.
- `stars`: The visual star rating. Use five characters such as `★★★★★`, `★★★★☆`, or `★★★☆☆`.

After the closing `---`, write the review in Markdown. The song layout already displays the title, performer, cover placeholder, and rating. Your Markdown body should contain the review paragraphs only.

Example body shape:

```markdown
Your first review paragraph goes here.

Your second review paragraph goes here.
```

You can use normal Markdown formatting, including headings, emphasis, links, blockquotes, and lists. Keep the review paragraphs reasonably short for comfortable reading on phones.

## Adding real cover images

The starter intentionally uses a designed placeholder so the site works without extra assets. To use your own image:

1. Create an `assets/images/` directory.
2. Add an image such as `assets/images/song-01.jpg`.
3. Add an `image` field to the song's front matter:

```yaml
image: "/assets/images/song-01.jpg"
```

4. In `_layouts/song.html`, replace the `song-cover` placeholder block with an image element, or add conditional Liquid like this:

```liquid
{% if page.image %}
  <img src="{{ page.image | relative_url }}" alt="Cover or related image for {{ page.title }}">
{% else %}
  <span class="cover-placeholder cover-placeholder--large">Cover image<br>placeholder</span>
{% endif %}
```

Remember to style the image with `width: 100%`, `height: 100%`, and `object-fit: cover`.

## Preview locally

Install Ruby and Bundler, then run:

```bash
bundle install
bundle exec jekyll serve --livereload
```

Open `http://localhost:4000` in your browser. Jekyll will rebuild the site when you save Markdown or template changes. Stop the server with `Ctrl+C`.

If you do not use Bundler, the equivalent command is:

```bash
jekyll serve --livereload
```

## Publish with GitHub Pages

1. Create a new GitHub repository. For a personal site, `YOUR-USERNAME.github.io` creates a user site. A normal repository creates a project site.
2. Upload or push every file in this folder to the repository's default branch.
3. In `_config.yml`, set `url` to your GitHub Pages domain. For a project site, set `baseurl` to the repository name, for example:

   ```yaml
   url: "https://YOUR-USERNAME.github.io"
   baseurl: "/YOUR-REPOSITORY"
   ```

   Leave `baseurl` empty for a user site.
4. In the repository, open **Settings → Pages**.
5. Under **Build and deployment**, choose **Deploy from a branch**, select your default branch and the `/ (root)` folder, then save.
6. Wait for the Pages deployment to finish. GitHub will show the published URL in the Pages settings.

The included site uses standard Jekyll features and does not require a plugin, so it works with GitHub Pages' normal build process.

## Updating the ranking

Edit the `rank` value in each `_songs/*.md` file. The home page automatically sorts the collection from rank 1 through rank 10. Keep every rank unique so the order is predictable.

## Customizing the look

- Change colors in the `:root` section of `assets/css/style.css`.
- Change fonts by editing the Google Fonts link in `_layouts/default.html` and the font-family declarations in the stylesheet.
- Update the home-page introduction in `index.md`.
- Change the footer text in `_layouts/default.html`.
