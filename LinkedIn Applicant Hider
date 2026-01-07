// ==UserScript==
// @name         LinkedIn Applicant Hider
// @namespace    http://tampermonkey.net/
// @version      1.0
// @description  Hides the "Number of applicants" and "People clicked apply" text on LinkedIn jobs to reduce application anxiety.
// @author       [Your Name/Username]
// @match        https://www.linkedin.com/*
// @grant        none
// @license      MIT
// ==/UserScript==

(function() {
    'use strict';

    // Configuration: Text patterns to hide
    const hidePatterns = [
        /(?:\d+|Over)\s+applicant/i,          // "123 applicants" or "Over 50 applicants"
        /(?:\d+|Over)\s+people\s+clicked/i,    // "Over 100 people clicked apply"
        /be\s+one\s+of\s+the\s+first/i         // "Be one of the first X applicants"
    ];

    function hideApplicantCounts() {
        // Select common text containers to scan
        const elements = document.querySelectorAll('span, p, div, li');

        elements.forEach(element => {
            // Optimization: Skip elements already hidden
            if (element.style.display === 'none') return;

            // Get text content safely
            const text = element.innerText || element.textContent;
            if (!text) return;

            // Check if text matches patterns
            const isMatch = hidePatterns.some(pattern => pattern.test(text));

            if (isMatch) {
                // Safety check: prevent hiding large blocks of text (like descriptions) that happen to contain keywords
                if (text.length < 100) {
                    element.style.display = 'none';
                }
            }
        });
    }

    // Initial run
    hideApplicantCounts();

    // Observe DOM changes (for infinite scrolling and dynamic navigation)
    const observer = new MutationObserver(() => {
        hideApplicantCounts();
    });

    observer.observe(document.body, {
        childList: true,
        subtree: true
    });

})();
