# Curve External Rewards

This repository's configuration files contain all metadata for projects to give external rewards for users of curve.

# This is a draft for a poosible data structure, this not production ready!

## Reward metadata structure

### Each reward metadata must have the following properties:

- `name`: Name of the reward campaign
- `description`: One-sentence description, not too long
- `imageId`: Filename of the app/tool's logo in the [`curve-assets`](https://github.com/curvefi/curve-assets/tree/main/platforms) repo
- `appUrl`: Link to the app/tool's Dashboard, or `null`
- `API`: Link to the API to display APR/Amount, or `null`
- `tags`: Array of relevant tags (any of the tags ids listed here: [`rewards-tags.json`](https://github.com/curvefi/curve-external-rewards/blob/main/rewards-tags.json)
- `networks`: Array of relevant networks
- pools: Array of relevant pools

  - `id`: internal id for you, or `null`
  - `timestampStart`: start of the rewards, as utc timestamp
  - `timestampEnd`: end of the rewards, as utc timestamp
  - "address": address of the pool
  - "gauge": address of the gauge, or `null`
  - "network": network of the reward
  - "dashboardLink": will be added to the appUrl
  - "multiplier": multiplier, or `null`
  - "APYLink": link to return APY, format should be XX.XX%, or `null`
  - "APRLink": link to return APR, format should be XX.XX%, or `null`
  - "amount": link to return amount of points, format should be "10'000 Points/Day", or `null`


### Example:

```json
{
  "name": "Points for LP",
  "description": "Points for liqudity provider of USDX",
  "imageId": "points_campaign_icon.png",
  "url": "https://points.finance/dashboard/",
  "API": "https://points.finance/api/apy/",
  "tags": ["points"],
  "networks" ["ethereum"],
  "pools": [{
    "id": "1",
    "timestampStart": "0",
    "timestampEnd": "0",
    "address": "0x0",
    "gauge": "0x0",
    "network": ["ethereum"],
    "dashboardLink": "?",
    "multiplier": "1",
    "APYLink": "/apy/0x0",
    "APRLink": "/apr/0x0",
    "amount": "amount/0x0
  }]
}
```

## Adding an rewards to the list

Conditions the project must meet in order to be added to the list of rewards:

1. It must fit the ["Curve rewards" definition](https://github.com/curvefi/curve-external-rewards/tree/main#curve-rewards)


2. It must be live

Easy two-step process for your reward to appear on Curve's websites:

1. You'll need to upload the app/tool's logo to the [`curve-assets` repo](https://github.com/curvefi/curve-assets/tree/main/platforms) (submit a PR there, we'll be notified and will review and merge it). Either an SVG image, or a PNG/JPG of at least 200x200 and at most 500x500 px.
2. Submit a PR in this very repository, adding the app/tool's metadata as described above in the [`rewards-list.json`](https://github.com/curvefi/curve-external-rewards/blob/main/rewards-list.json) file. You don't have to wait for (1) to be merged to do this. We'll also be notified and will review and merge your PR. *Please provide a very short explanation of how the submitted project fits into the ["Curve integration" definition](https://github.com/curvefi/curve-external-rewards/tree/main#curve-rewards), if it isn't immediately obvious from the project's metadata in your PR.*
