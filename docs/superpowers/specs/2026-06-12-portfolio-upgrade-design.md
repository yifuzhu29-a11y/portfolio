# Portfolio Upgrade Design

## Goal

Create a separate, polished job-seeking portfolio page for Zhu Yifu without modifying the existing `index.html`.

## Direction

Use a professional one-page resume and portfolio structure. The page should make the target role clear immediately, then support it with practical evidence: AIGC video workflow, short-video operation results, animation production leadership, tool stack, education, and contact information.

## Content Structure

- Hero: name, target role, location, education status, availability, and concise pitch.
- Proof points: complete AI video workflow, short-video operation result, 3D animation leadership, and design/video foundation.
- Featured projects: AI live-action short drama, animation `熠`, doctor Douyin account operation, and community service PBL.
- Workflow: script breakdown, storyboard, image/video generation, iteration, editing, delivery.
- Experience and education: timeline-style summary.
- Contact: email, phone, WeChat.

## Visual Design

Use a calm professional palette with warm off-white, dark ink text, muted matcha green, and restrained coffee accent. The layout should feel more like a recruiter-ready portfolio than an editable internal tool. Use local media only, including `bg-video.mp4` and the existing reference image when useful.

## Constraints

- Create a new file: `portfolio-upgraded.html`.
- Do not modify `index.html`.
- Keep the page self-contained with HTML, CSS, and small JavaScript only.
- Do not use external libraries, CDN assets, or network resources.
- Must be readable on desktop and mobile.
