# CGBB plugin package for the ChatGPT plugin directory

Upload as a ZIP of this folder's contents (plugin.json at the ZIP root).

Before submitting, IT must:
1. Replace `TO_BE_ADDED_BY_IT` in plugin.json (`review.demo_recording_url`) with a reviewer-accessible link to a screen recording of the 5 positive and 3 negative test cases, run in ChatGPT with this connector.
2. Pick the category from the dashboard list if "Business" is not offered.
3. Domain challenge: set the token shown in the portal as the Cloudflare Worker secret `OPENAI_APPS_CHALLENGE` on worker `cgbb-diagnosis` (Settings > Variables and Secrets > Add > Secret). It is then served as plain text at https://api.cgbb.org/.well-known/openai-apps-challenge. No code change needed.

Test cases use the Secretariat mailbox (secretariat@cgbb.org) as the contact email, so confirmation emails from reviewer tests land there, not with a stranger.
