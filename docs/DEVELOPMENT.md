# Development Documentation 🛠️

This document outlines the technical details and development workflow for the **Wally Worner Storybook**.

## 🏗️ Architecture

The application is built as a **Single Page Application (SPA)** contained primarily within `index.html`. This "monolithic" approach was chosen for simplicity of distribution and ease of editing.

### Key Components

1.  **State Management**:
    *   Simple global variables track the application state:
        *   `currentPage`: Index of the currently visible page.
        *   `soundEnabled`: Boolean flag for audio mute/unmute.
        *   `rabbitCount`: Integer tracking the score of the minigame.

2.  **Page Transition System**:
    *   Pages are `div.page` elements hidden by default (`display: none`).
    *   The `active` class is toggled to show the current page.
    *   CSS Animation `pageFlip` (3D transform `rotateY`) provides the book-turning effect.

3.  **Asset Management**:
    *   Images are stored in `assets/images/`.
    *   Audio is loaded from external CDNs (Mixkit) to keep the repository light, though local fallback support is structured.

## 🎨 Styling & Design System

*   **Fonts**:
    *   *Chewy*: Headlines and Titles (Playful, bold).
    *   *Patrick Hand*: Body text (Handwritten style).
*   **Color Palette**:
    *   Primary: `#800000` (Deep Red - Maltese Cross Color)
    *   Secondary: `#FFD700` (Gold - Victory/Celebration)
    *   Backgrounds: `#2c1810` (Dark Wood), `#f4e4bc` (Parchment)

## 🧩 Adding New Content

### Adding a New Page
To add a new page to the story:
1.  Copy an existing `<div class="page">` block in `index.html`.
2.  Update the `h1` and `p` content.
3.  Update the `.page-number`.
4.  The JavaScript function `nextPage()` automatically detects the new total number of pages, so no JS changes are needed for simple page additions.

### Adding New Sounds
1.  Add a new `<audio>` tag with a unique ID in the `body`.
2.  Update the `playSound(type)` function in the `<script>` section to map a new keyword (e.g., `'dragon'`) to the new audio ID.

## 🧪 Testing

*   **Browser Compatibility**: Tested on Chrome, Safari, and Firefox.
*   **Responsiveness**: The book container scales using `vw/vh` and media queries to adapt from desktop (double-page spread) to mobile (single column).

## 🔮 Future Roadmap

*   **Book Two**: Implementation of "Siege of Malta 1940-1943" (Draft started in `docs/drafts/book2.md`).
*   **Voiceover**: Adding `TTS` or recorded narration for accessibility.
*   **PWA**: Converting the site to a Progressive Web App for offline installation on tablets.
