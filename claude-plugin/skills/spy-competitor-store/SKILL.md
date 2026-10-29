---
name: spy-competitor-store
description: Look at the Facebook video ads a competitor store or Facebook Page is running - live and new ads, top videos with their real age, and how many other stores use the same videos. Use when the user gives a store domain or Facebook Page and asks what ads it runs, what it is testing, or which of its videos are copied.
---

# Spy on a competitor store

## Steps

1. For a store domain, call `spywin_spy_store_ads`. For a Facebook Page link or ID, call `spywin_get_page_ads` (it also lists the stores the Page sends traffic to).
2. If the user wants detail on one of the top videos and the result includes its ad link, call `spywin_lookup_video_ad` for that video only.
3. If the user wants to copy one of the store's products to their own Shopify, call `spywin_export_shopify_product` with that product's URL. It only reads public product pages.

## Report

Answer in the user's language:

- **Activity:** live ads, new ads in the last 7 days, number of videos, products and Pages, and the first ad date in the library.
- **Top videos:** for each, its real age (when the file was first uploaded to Facebook) and how many stores run it. Split them into videos that look new and few stores use, and videos that are old or run by many stores (copied).
- **Read:** a short, neutral summary of what the store seems to be focusing on. A burst of new ads means active testing, not success.
- **Limits:** data covers Meta ads shown in the US from the SpyWinAds library; counts are minimums of ads observed; there is no ad spend, reach, order or revenue data.

## Don't

- Don't claim the store is profitable or that a product is its best seller.
- Don't guess numbers that aren't in the result, and don't present "earliest store" as the owner of a video.
