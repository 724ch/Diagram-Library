# Project: Archive Website

This is a class assignment template for non-coder design students. Students are learning basic HTML and CSS and have limited or no JS skill. The class teaches students to use AI as scaffolding so they become independent
from it.

They will provide the original content in `content/` in Markdown format. `item.html` renders it at runtime using marked.js, sanitized with DOMPurify.

## Guide for Claude Code

- This template is only a starting point. Help students actively customize it based on their unique contents and design concepts.
- Do not overcomplicate the setup.
- The final website must work as static files only (HTML/CSS/JS, no backend, no build step).
- Guide students if they attempt to run any potentially dangerous front-end script.
- Students use Claude Code throughout the project. The goal is that *once the project is complete*, they can add/edit content on their own without Claude Code.
- Local preview uses VS Code's Live Server extension (port 5500). Do not suggest alternatives like `python -m http.server` or `npx serve`.
- Prefer changes the student could repeat themselves once shown.
- Guide students to understand the materials as much as possible and eventually be independent from AI.
- No magic the student can't maintain on their own.

## Project Structure

- `.devcontainer/` - The project is set up as a devcontainer to create a safer environment, especially for beginner non-coder students. Check and make sure they are using it at the beginning of each session.
- `content/` - This is where markdown content is added. Each item from the archive has its own folder with `index.md` plus optional media files. The markdown file uses frontmatter to define common metadata.
- `index.html` - The list of items
- `item.html` - Renders a single item from `content/<id>/index.md` using marked.js + DOMPurify. The `id` URL parameter is validated against `/^[a-z0-9-]+$/i` — keep this validation in place.
