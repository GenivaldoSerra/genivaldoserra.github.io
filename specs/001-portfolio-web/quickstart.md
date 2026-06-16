# Quickstart Validation Guide

## Prerequisites
- A modern web browser (Chrome, Firefox, Safari, Edge).
- A local web server to serve static files (optional, but recommended to test absolute paths, e.g., `python3 -m http.server 8000` or VSCode Live Server).

## Setup
1. Clone the repository.
2. Navigate to the project root directory.

## Running
1. Open `index.html` directly in your browser OR
2. Run a local server: `python3 -m http.server 8000` and visit `http://localhost:8000`

## Validation Scenarios
1. **Responsiveness**: Resize the browser window from desktop width (1200px+) down to mobile width (320px). Ensure the project grid collapses from 3 columns to 1 column without any horizontal scrolling.
2. **Navigation**: Click on the "Engenharia de Dados" and "DevOps" links in the navbar. Verify the page scrolls smoothly to the correct sections.
3. **External Links**: Click on any project's "Ver no GitHub" button or the footer social links. Verify they open in a new tab (`target="_blank"`).
4. **Visual Identity**: Verify that the primary accent color is the vibrant green (`#00D84F`) on hover states and call-to-action buttons.
