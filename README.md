# HelloFreshCrawler

Recipe crawler for the popular HelloFresh meal-kit provider.

Supports crawling on US, GB, FR and DE recipe archives that are publicly available on www.hellofresh.com.

### Features

- **Multi-Language Support:** Crawls recipe archives in English (US), English (GB), French (FR) and German (DE).

- **Automatic Retries:** Downloads that fail due to transient network errors (e.g. timeouts, connection resets) are retried up to 3 times. Downloads that still fail are reported in a summary when the crawl finishes.

- **Contributors:** 
  - [@alexcodito](https://github.com/alexcodito/) (Author)
  - [@kevinrodd](https://github.com/kevinrodd/)

### Usage

`node index.js HelloFresh -l GB -s ./downloads`

The above will download every PDF recipe card from the specified country's archive into the specified local directory.

| Option | Alias | Description | Default |
| --- | --- | --- | --- |
| `--locale` | `-l` | Locale to crawl on. One of `US`, `GB`, `DE`, `FR`. | `US` |
| `--recipeCardSaveDirectory` | `-s` | Directory where to save the downloaded PDF recipe cards. | `./recipe-card-pdfs` |
| `--maxPrepTime` | `-m` | Maximum recipe prep time in minutes. No limit applied if omitted. | No limit |
| `--product` | `-p` | Pipe-separated list of product types to include (e.g. `classic-box\|veggie-box\|family-box`). | `classic-box\|veggie-box\|family-box` |

<img src="https://github.com/alexcodito/HelloFreshCrawler/blob/master/hello-fresh-crawler.gif" width="886" alt="HelloFresh Crawler Demo"/>

### Notes

- The HelloFresh API provides extensive JSON metadata, including ingredients, nutrition, units and ratings. Storing this in a document database could enable useful applications such as:

  - Generating grocery lists from selected recipes
  - Advanced search criteria (e.g. total cooking time, calories, excluding/including ingredients etc.)
