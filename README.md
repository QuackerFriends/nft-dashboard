# NFT Signal Dashboard

Real-time NFT buy/sell signal dashboard powered by Moralis. Tracks floor price, volume, bid pressure, and your wallet positions with tiered exit alerts.

## How to deploy to GitHub Pages

### Step 1 — Create a GitHub account
Go to github.com and sign up if you don't have one. It's free.

### Step 2 — Create a new repository
1. Click the + button in the top right corner
2. Select "New repository"
3. Name it: `nft-dashboard`
4. Set it to **Public**
5. Click "Create repository"

### Step 3 — Upload the files
1. On your new repository page, click "uploading an existing file"
2. Drag and drop both `index.html` and `README.md` into the box
3. Click "Commit changes"

### Step 4 — Enable GitHub Pages
1. Go to your repository Settings tab
2. Scroll down to the "Pages" section in the left sidebar
3. Under "Source", select "Deploy from a branch"
4. Select branch: `main`
5. Select folder: `/ (root)`
6. Click Save

### Step 5 — Your site is live
GitHub will give you a URL like:
`https://yourusername.github.io/nft-dashboard`

It takes about 60 seconds to go live after saving.

## How to use the dashboard

1. Open your GitHub Pages URL
2. Paste your Moralis API key into the config panel
3. Your wallet address is pre-filled — update it if needed
4. If you bought an NFT via accepting an offer, enter your offer price in the manual price field
5. Hit "Refresh data" — all data loads live from Moralis

## Configuration

| Field | Description |
|---|---|
| Moralis API key | Get free at admin.moralis.com |
| Wallet address | Your ETH wallet (0x...) |
| Stop-loss % | Alert if floor drops this % below your entry |
| Manual entry price | Use if you bought via offer (value shows as 0 on-chain) |

## Adding more collections

Open `index.html` and find this section near the top of the script:

```js
const COLLECTIONS = {
  'Still Alive': '0x52caee4275765dde6f47f874e7cf8181f5b5e5da',
  'Gorgez':      '0x6339e5e072086621540d0362c4e3cea0d643e114',
};
```

Add any collection by pasting its contract address. Find the contract address on OpenSea by clicking any NFT in the collection and scrolling to the Details section.

## Exit signal logic

| Score | Verdict |
|---|---|
| +4 or above | BUY SIGNAL |
| -3 or below | EXIT RISK |
| Between | HOLD / WATCH |

Profit tiers: 1.5x early exit · 2x main target · 4x moon bag

## Security note

Your Moralis API key is entered in the browser and is never stored or sent anywhere except directly to the Moralis API. Regenerate your key periodically from your Moralis dashboard.
