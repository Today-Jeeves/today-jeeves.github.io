# How new articles get published

A scheduled Claude routine runs this playbook. Nobody needs to touch the repo.

## Each run

1. Pull `main`. Read `_config.yml`, the list of existing posts in `_posts/`, and `TOPICS.md`.
2. Pick the first unchecked topic in `TOPICS.md` that doesn't overlap an existing post. If the list runs low, add 10 new topics first (specific, search-shaped questions people actually ask about budgeting, debt, saving, credit, banking basics or money habits; no investing tips, no tax or legal advice).
3. Write ONE article, 1,200 to 2,000 words, to `_posts/YYYY-MM-DD-slug.md` (today's date, short slug from the main search phrase). Front matter: `title`, `description` (under 160 characters), `summary` (1 to 2 sentences), `category` (Budgeting, Debt, Saving, Credit or Money habits).
4. Article rules:
   - Lead with a bold "The short answer:" paragraph that actually answers the question.
   - Practical steps and at least one worked example with real numbers. Run every calculation in Python before publishing it; never guess numbers.
   - Only state facts you are confident are current. Prefer stable rules over figures that change yearly; if a yearly figure is needed (IRS limits, rates), say which year and link the primary source (irs.gov, consumerfinance.gov, fdic.gov, ftc.gov). Check that every external link returns 200.
   - Link 2 to 4 existing posts where relevant, using `/slug/` paths.
   - No fake personal stories, invented statistics, invented quotes, or claims of testing products.
   - No mention of the kit in the body unless it fits naturally; the layout already adds the kit box and the disclosure.
   - Affiliate product links only via `{% include amazon.html asin="..." text="..." %}` and only for products genuinely relevant to the article, at most 3 per article.
5. Build with `jekyll build` and fix any error. Check the new page's internal links resolve in `_site/`.
6. Tick the topic in `TOPICS.md`, commit as "Add article: <title>", push to `main`. GitHub Pages publishes automatically.
7. Monthly (first run of the month): refresh one older article if anything in it has gone out of date, and bump its `last_modified_at`.
