# CryptoPriceScraper

A small solution for scraping real-time cryptocurrency prices from a popular aggregator in a stealthy manner, designed for seamless integration with Excel through local API.
 The API point is located at `http://localhost:4200/api/price` 

## Features ✨
- **Undetectable Scraping**  
  Uses `puppeteer-extra` with stealth plugin to mimic human behavior
- **On-Demand Execution**  
  Scraping triggers only when API endpoint is called
- **Headless Browser**  
  Runs invisibly with `headless: true` mode
- **Persistent Storage**  
  Maintains price history in `scraped_data/prices.txt`
-  **Customizable Assets:** Accepts a comma-separated list of coins via command-line arguments. 

## Prerequisites

- Node.js (v22 or later is recommended)
- npm

## Installation

1. **Clone the repository:**

   ```bash
   git clone https://github.com/danzin/CryptoPriceScraper.git
   cd CryptoPriceScraper
   ```
2. **Install dependencies:**
   
   `npm install`
4. **Usage:**
   
   The application uses yargs to parse command-line arguments. By default, without the `--coins` option, it tracks bitcoin, ethereum, and solana.
   
   To start the server:
   `node server.js --coins=coin1,coin2,coin3,etc`
   
   It doesn't support tickers. Use the full name of the asset.

## Excel integration 

 1. Open the Data tab -> Click 'From web' -> Use the API url in the URL field: 

![image](https://github.com/user-attachments/assets/f76c2762-a809-4113-b7eb-cde705a93ad1)

2. Right click on the Record field in the 'Power Query Editor -> Into Table:

![image](https://github.com/user-attachments/assets/d04e1a0a-24ff-4d17-a9b1-f28a65c73a67)

3. Spread the table -> select assets -> click Okay:

![image](https://github.com/user-attachments/assets/ac0291df-6cf9-44c8-87af-4650de31251e)

4. 'Close & Load': 

![image](https://github.com/user-attachments/assets/7595bb10-438c-45fd-a996-c9a79a93ff1e)

5. Current prices are loaded into a separate table:

![image](https://github.com/user-attachments/assets/bc14928f-bcc4-429f-b6a8-da97e1844e05)

6. Data can be refreshed manually from the 'Refresh all' button, or on intervals/in the background from the query properties:

![image](https://github.com/user-attachments/assets/aaf04903-24af-44a5-9f44-36dd2210118e)



**Warning: Adding lots of assets can become resource heavy. The scraper spins a separate headless browser for every single asset.**
