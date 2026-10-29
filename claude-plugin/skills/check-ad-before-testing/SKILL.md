---
name: check-ad-before-testing
description: Check a Facebook video ad before testing the product it sells - how old the video really is, how many stores already run it, and which stores ran it first. Use when the user shares a Meta Ad Library link or ad ID, or asks whether a product or video ad is new, old, saturated or worth testing.
---

# Check an ad before testing

Sellers often see a "new" ad and rush to test the product, when the video is months old and dozens of stores already ran it. This skill answers four questions with SpyWinAds data, then states plainly what the data can't tell.

## Steps

1. Call `spywin_lookup_video_ad` with the Ad Library link or ad ID.
2. If the user names their own store or a competitor, or the earliest store looks relevant, call `spywin_spy_store_ads` on that domain for context. Don't call it for every store in the list.
3. If the user asks how this compares with the market, call `spywin_get_video_reuse_research` and use its numbers as background.

## Report

Answer in the user's language, in this order:

- **How old is the video?** The day the video file was first uploaded to Facebook, and the first ad date. If the upload is weeks or months before the first ad, say the video was made earlier and brought back, not new.
- **How far has it spread?** Stores running it now and ever, and live ads. Say these are minimums of ads SpyWinAds has seen.
- **Who ran it first?** The earliest stores in the SpyWinAds library with their first ad dates. Say "earliest in the library", never "the owner" or "the original".
- **What this means for testing:** a short, neutral read. For example: many stores and an old file mean the video is widely copied and late to join; a fresh file with one or two stores means it is early. Present this as a signal, not a verdict.
- **What the data can't tell:** SpyWinAds has no ad spend, reach, orders or revenue data, so it can't show whether the product sells or makes a profit. Many live or new ads can mean heavy testing, and a video run by many stores is copied, not proven.

## Don't

- Don't call a product a "winner", "proven" or "profitable", or estimate sales or profit.
- Don't name the earliest store as the creator or owner of the video.
- Don't invent numbers the tool didn't return. If a field is missing, say it's not in the library.
- If the tool says the daily limit is reached, tell the user when it resets and stop.
