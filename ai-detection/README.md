# AI Content Detection: 2026 NDP Leadership Race

AI-generated content detection results for campaign materials and convention speeches from the 2026 NDP federal leadership race, using the [Pangram Labs](https://pangramlabs.com) API v3.2.

## Summary

| Source | Documents | AI-Flagged |
|---|---|---|
| Lewis campaign website (lewisforleader.ca) | 20 | 0 |
| McPherson campaign website (heathermcpherson.ca) | 5 | 2 |
| Convention speeches (CPAC transcripts) | 3 | 0 |
| **Total** | **28** | **2** |

### Flagged documents

| File | AI Score | Confidence | Words |
|---|---|---|---|
| McPherson — Homepage/bio (`index.txt`) | 66.6% | Medium | 160 |
| McPherson — Housing policy (`housing.txt`) | 78.3% | Low | 53 |

All other documents were classified as fully human-written with high confidence.

## Method

- Campaign websites were scraped and cleaned of navigation/boilerplate
- Convention speeches were transcribed from CPAC video using Deepgram (whisper-medium model), then cleaned of crowd noise
- Each document was submitted individually to the Pangram Labs text detection API v3
- French-language pages were excluded
- Files under 50 words were excluded (except `housing.txt` at 53 words, which is near the threshold)

## Files

- `lewis-campaign/` — 20 JSON responses for lewisforleader.ca English pages
- `mcpherson-campaign/` — 5 JSON responses for heathermcpherson.ca pages
- `speeches/` — 3 JSON responses for convention speech transcripts

## Notes

- The `housing.txt` flag should be interpreted cautiously: 53 words is near the minimum viable length for AI detection, and Pangram reported low confidence.
- The `index.txt` bio page is a stronger signal at 160 words and medium confidence, with stylistic markers (thematic bookending, polished parallel structure) consistent with AI-assisted writing.
- Lewis's campaign produced ~20,000 words of detailed policy content, all classified as human-written.
- Detection was run on April 1, 2026.
