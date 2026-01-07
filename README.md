LinkedIn Applicant Hider

A lightweight Tampermonkey userscript that removes the “Number of applicants” and “People clicked apply” counters from LinkedIn job postings.

🎯 Why?

Applying for jobs is stressful enough without seeing “Over 200 applicants” on every listing.

LinkedIn often surfaces these numbers to create urgency and FOMO. For many candidates, they’re simply distracting and discouraging. This script hides those metrics so you can focus on the job description, not the competition.

🚀 Installation

Install the Tampermonkey browser extension:
https://www.tampermonkey.net/

(Available for Chrome, Firefox, Edge, and Safari)

Open the script file in this repository:
linkedin_hider.user.js

Click Raw.

Tampermonkey will automatically prompt you to Install the script.

⚙️ How It Works

Unlike many CSS-only solutions, this script does not rely on LinkedIn’s frequently changing and obfuscated class names (for example: .job-card__applicant-count).

Instead, it uses text-based pattern matching:

Scans the page for phrases like:

“applicants”

“people clicked apply”

Hides only the matching elements

Uses a MutationObserver to keep counts hidden as:

You scroll

You open new job postings

LinkedIn dynamically updates the page

This makes the script more resilient to LinkedIn UI changes.

🔒 Privacy & Security

Local execution only — runs entirely in your browser

No data collection — nothing is tracked, stored, or transmitted

Restricted scope — only runs on linkedin.com domains
