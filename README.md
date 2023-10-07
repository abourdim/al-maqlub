# المقلوب · Al-Maqlub

**Arabic Reversible Poetry — Museum · Creator · Game · Reciter**

Part of the **كلامي (Kalami)** Arabic tools family.

---

## Overview

Al-Maqlub (المقلوب, "The Reversed") is a single-file browser application dedicated to the ancient Arabic art of palindrome poetry. It brings together four experiences in one interface: a curated museum of classical palindromes, a real-time composition studio, an interactive puzzle game, and a dual-direction reciter that speaks poems forward and backward.

Arabic palindrome poetry is one of the most technically demanding forms in the Arabic literary tradition. Known historically as المقلوب الحرفي (letter reversal), السرطاني (the crab poem), and other names, these compositions read identically — or produce new meaning — when reversed. Al-Maqlub makes this tradition accessible, interactive, and beautiful.

---

## Features

### 📖 المكتبة · Library

The Library holds 10 verified classical Arabic palindromes, each displayed on a decorated card with:

- Large Arabic text in Amiri calligraphic font
- Type badge indicating the palindrome category
- English and French translations
- Century and source attribution
- **Symmetry axis animation** — the signature visual: a gold vertical line marks the center while matching mirror pairs illuminate gold simultaneously, mismatches glow crimson
- Forward/backward text toggle with smooth animation
- Text-to-speech button (reads aloud in ar-SA)

The four palindrome types represented:

| Type | Arabic | Description |
|------|--------|-------------|
| Letter palindrome | المقلوب الحرفي | Same letter sequence forwards and backwards |
| Crab poem | السرطاني | Word order reverses to produce valid text |
| Sentence palindrome | المستوي | Full sentence reads same in both directions |
| Half-verse mirror | شطر مقلوب | One hemistich mirrors the other |

### ✍️ المحرر · Creator

The Creator is a composition studio for writing your own palindromes:

- Large Arabic text input area (RTL, Amiri font)
- Full Arabic virtual keyboard: 28 letters, Arabic numerals (٠–٩), punctuation (،؟!.), backspace, word-delete, space bar
- Microphone input via Web Speech API (ar-SA continuous recognition)
- **Real-time analysis** updating as you type:
  - Letter palindrome check (✓/✗)
  - Word palindrome check (✓/✗)
  - Symmetry score 0–100% with animated progress arc
  - Color-coded letter map: gold = matching mirror pair, crimson = mismatch
  - Fix suggestions panel showing which positions to correct
- Save compositions to a session collection
- Export any text as a decorative SVG card

### 🎮 اللعبة · Game

The Game tests your knowledge of Arabic palindrome structure:

- **3 difficulty levels:**
  - حروف (Letters) — fill in 1–3 missing letters
  - كلمات (Words) — fill in missing word(s)
  - بيت (Full verse) — reconstruct the entire mirror half
- Puzzles drawn randomly from the Library collection
- Arabic virtual keyboard for input
- Instant visual feedback: correct answers get a gold glow with particle burst, wrong answers get a crimson shake showing the correct answer
- Running score counter and streak badge
- Optional 30-second timer mode

### 🔊 المنشد · Reciter

The Reciter brings palindromes to life through speech:

- Select any poem from the Library dropdown, or paste custom Arabic text
- **Three playback modes:**
  - ▶ Forward — reads the poem naturally, each letter highlights gold
  - ◀ Backward — reads reversed, letters highlight crimson
  - ⏯ Dual — plays forward, pauses 500ms, then plays backward
- Speed slider from 0.5× to 2×
- Animated waveform bars synchronized to playback
- Letter-by-letter highlight timing estimated from character count and speech rate

---

## How To Use

### Getting Started

1. Download `almaqlub.html` (or the full zip package)
2. Open `almaqlub.html` in Chrome or Edge for full functionality
3. The app loads directly — no server, no installation, no build step

### Navigating Sections

Click any of the four tabs at the top to switch between المكتبة (Library), المحرر (Creator), اللعبة (Game), and المنشد (Reciter). Only one section is visible at a time.

### Using the Library

- Scroll through the poem cards to browse the collection
- Hover over a card to see the gold accent line appear at the top
- Click **تحليل** (Analyze) on any card to trigger the symmetry animation — watch as matching letter pairs light up from center outward
- Click **عكس** (Reverse) to flip the text backwards and see the palindrome in action
- Click **استمع** (Listen) to hear the poem read aloud via text-to-speech

### Composing in the Creator

- Type Arabic text directly using your system keyboard, or use the on-screen Arabic keyboard
- Click **تسجيل** (Record) to dictate via microphone (Chrome/Edge only)
- Watch the analysis panel update in real time as you type
- The letter map below shows every character color-coded: gold = matches mirror position, crimson = mismatch
- Check the suggestions panel for specific guidance on which positions to fix
- When satisfied, click **حفظ** (Save) to add to your session collection, or **تصدير SVG** (Export SVG) to download as a decorative image

### Playing the Game

- Choose your difficulty level: حروف, كلمات, or بيت
- Optionally enable the timer with the ⏱ button
- Read the poem with blanks and type your answer in the input field (or use the keyboard)
- Click **تحقق** (Check) to submit
- Click **التالي** (Next) for a new puzzle
- Build the longest streak you can!

### Using the Reciter

- Select a poem from the dropdown, or paste any Arabic text in the text area below
- Choose a playback mode: forward, backward, or dual
- Adjust the speed slider before or during playback
- Click **إيقاف** (Stop) to halt playback at any time
- In dual mode, the forward pass plays first (gold), a brief pause, then the backward pass (crimson)

---

## Frequently Asked Questions

### General

**Q: Do I need an internet connection?**
A: Only for loading Google Fonts (Amiri, Cinzel, DM Mono) and for text-to-speech. The core palindrome logic, keyboard, game, and analysis all work offline. If fonts fail to load, the browser falls back to serif/monospace.

**Q: Which browser should I use?**
A: Chrome or Edge for the full experience (speech recognition + synthesis). Firefox supports TTS but not microphone input. Safari has partial support.

**Q: Can I use this on mobile?**
A: Yes. The layout is fully responsive. The on-screen Arabic keyboard works with touch. Speech features depend on mobile browser support.

**Q: Is the data saved between sessions?**
A: Saved compositions in the Creator use session storage, which persists within a single browser tab session. Closing the tab clears saved items. Game scores also reset on page reload.

**Q: Can I add my own poems to the Library?**
A: Not through the UI currently. You can edit the `POEMS` array in the source code to add new entries. Each entry needs `text`, `type`, `typeName`, `en`, `fr`, `source`, and `century` fields.

### Library

**Q: Are all the palindromes verified?**
A: Yes. Every poem has been tested against the `stripForCompare` + `isLetterPalindrome` / `isWordPalindrome` functions. Stripping removes tashkeel, tatweel, spaces, punctuation, and normalizes alef/hamza variants before comparison.

**Q: What does the symmetry animation show?**
A: It reveals the mirror structure of the palindrome. Starting from the center, each pair of letters at positions (i) and (length−1−i) illuminates simultaneously. Gold = match, crimson = mismatch. A vertical gold line marks the axis of symmetry.

**Q: Why do some poems have "Reconstructed" in the source?**
A: A few poems are reconstructions in the classical style rather than direct quotations from named historical manuscripts. They are labeled clearly.

**Q: What is the difference between letter and word palindromes?**
A: A letter palindrome reads the same character-by-character when reversed (after stripping diacritics and spaces). A word palindrome has the same sequence of words when the word order is reversed. For example, "وَدِّعْ سُعَاد وَدِّعْ" — the three words in reverse order are the same three words.

### Creator

**Q: What exactly gets stripped for palindrome comparison?**
A: The function removes: tashkeel/diacritics (Unicode 0610–061A, 064B–065F, 0670, 06D6–06DC), tatweel (0640), all whitespace, Arabic and Latin punctuation (،؟!,.?), and normalizes alef variants (إأآ → ا) and hamza carriers (ؤئ → ء). The original text with diacritics is always preserved for display.

**Q: My text shows 95% symmetry — what does that mean?**
A: The symmetry score counts how many mirror-position letter pairs match, divided by the total number of pairs. 95% means most pairs match but a few positions differ. Check the crimson-highlighted letters in the letter map to see exactly which to adjust.

**Q: How does the SVG export work?**
A: It generates a standalone SVG file with your text on a dark background with gold border, including the symmetry score. The file downloads automatically and can be opened in any image viewer or embedded in documents.

**Q: Can I use the microphone for dictation?**
A: Yes, but only in Chrome or Edge. Click the تسجيل button, grant mic permission, and speak. The recognized text appears in the input area and analysis updates in real time. Click إيقاف to stop recording.

### Game

**Q: Where do the puzzles come from?**
A: All puzzles are generated from the 10 poems in the Library. The app randomly selects a poem and blanks out letters, words, or half the verse depending on difficulty.

**Q: How is scoring calculated?**
A: Letters difficulty: 10 points. Words: 25 points. Full verse: 50 points. Streak tracks consecutive correct answers and resets to zero on any wrong answer.

**Q: Does the timer affect scoring?**
A: No. The timer is a challenge mode only. If time runs out, the answer is marked wrong (streak resets) but no points are deducted.

**Q: The game seems too easy / too hard.**
A: Try switching difficulty levels. "حروف" is accessible for beginners, while "بيت" requires deep familiarity with the poems. Timer mode adds pressure at any level.

### Reciter

**Q: Why doesn't the text-to-speech sound right?**
A: TTS quality depends on your browser's available Arabic voices. Chrome typically has the best ar-SA voices. Classical palindromes may not always be pronounced as intended by the TTS engine.

**Q: Can I recite my own text?**
A: Yes. Paste or type any Arabic text into the custom text area. It does not need to be a palindrome — the reciter will play any text forward and backward.

**Q: What happens in dual mode?**
A: Forward pass with gold highlights, 500ms pause, then backward pass with crimson highlights. This audibly demonstrates the palindrome property.

---

## Help & Troubleshooting

### No sound when clicking Listen/Play

- Check that your browser volume is not muted
- Try Chrome or Edge — they have the best Arabic TTS support
- On first use, you may need to click anywhere on the page before audio plays (browser autoplay policy)
- Open browser console and run `speechSynthesis.getVoices()` to verify Arabic voices are available

### Microphone not working

- Speech recognition requires Chrome or Edge (`webkitSpeechRecognition` API)
- Grant microphone permission when the browser prompts
- HTTPS is required on most browsers; opening as a local file usually works
- Firefox and Safari do not support Web Speech Recognition

### Arabic keyboard keys not appearing

- Ensure Google Fonts loaded (check the browser network tab)
- Keys still function even with fallback fonts — only the visual appearance changes
- Try hard-refreshing: Ctrl+Shift+R (Windows/Linux) or Cmd+Shift+R (Mac)

### Game shows no puzzle

- Navigate to the Game tab — the first puzzle generates automatically
- If the display is empty, click "التالي" (Next) to generate a new one

### SVG export looks different from the app

- The SVG export is a simplified card — it does not include the symmetry animation or letter map
- The exported SVG uses inline styles and renders in any SVG-capable viewer

### Performance issues on mobile

- The geometric background canvas runs continuously. On very old devices this may cause lag
- The animation is decorative at 12% opacity — core functionality is unaffected
- You can disable the canvas by adding `#geoCanvas { display: none; }` in the browser dev tools

### Text direction looks wrong

- The app sets `dir="rtl"` on the HTML root element
- If text appears left-to-right, check that your browser is not overriding page direction
- All input fields are explicitly set to RTL

---

## Technical Reference

### Architecture

Single HTML file (~65KB) containing:
- **CSS** — all styles inline in a `<style>` block, CSS custom properties for the design system, responsive breakpoint at 600px
- **HTML** — semantic structure with four `<section>` elements toggled by navigation, `<canvas>` for geometric background
- **JavaScript** — all logic inline in a `<script>` block, no modules, no bundler, no framework

### Core Functions

```javascript
// Strip diacritics, tatweel, spaces, punctuation, normalize alef/hamza
function stripForCompare(str) {
  return str
    .replace(/[\u0610-\u061A\u064B-\u065F\u0670\u06D6-\u06DC]/g, '')
    .replace(/[\u0640]/g, '')
    .replace(/\s+/g, '')
    .replace(/[،؟!,.?]/g, '')
    .replace(/[إأآا]/g, 'ا')
    .replace(/[ؤئ]/g, 'ء')
    .trim();
}

// Letter-by-letter palindrome check
function isLetterPalindrome(str) {
  const s = stripForCompare(str);
  return s === s.split('').reverse().join('');
}

// Word-by-word palindrome check (strips each word before comparing)
function isWordPalindrome(str) {
  const stripped = str.trim().split(/\s+/).map(w => stripForCompare(w));
  const rev = [...stripped].reverse();
  return stripped.join(' ') === rev.join(' ');
}

// Symmetry score: percentage of matching mirror pairs (0–100)
function symmetryScore(str) { ... }
```

### External Resources

| Resource | URL | Purpose |
|----------|-----|---------|
| Google Fonts | `fonts.googleapis.com` | Amiri, Cinzel, DM Mono |
| Web Speech API | Browser native | SpeechRecognition (ar-SA), SpeechSynthesis (ar-SA) |
| Canvas 2D | Browser native | Geometric background animation |

### CSS Custom Properties

```css
--void:    #030508    /* deepest background */
--deep:    #07101e    /* component backgrounds */
--surface: #0c1828    /* card backgrounds */
--gold:    #c8922a    /* primary accent */
--gold2:   #e8b84b    /* highlight accent */
--gold3:   #f5d98a    /* light accent */
--crimson: #8b2020    /* error/mismatch dark */
--crimson2:#c0392b    /* error/mismatch bright */
--teal:    #1a9f88    /* success/correct */
--text:    #e8dcc8    /* primary text */
--text2:   #9a8870    /* secondary text */
--border:  rgba(200,146,42,.18)  /* subtle borders */
```

### Browser Compatibility

| Feature | Chrome | Edge | Firefox | Safari |
|---------|--------|------|---------|--------|
| Core app | ✓ | ✓ | ✓ | ✓ |
| Arabic keyboard | ✓ | ✓ | ✓ | ✓ |
| Palindrome analysis | ✓ | ✓ | ✓ | ✓ |
| Game | ✓ | ✓ | ✓ | ✓ |
| Text-to-speech | ✓ | ✓ | ✓ | Partial |
| Speech recognition | ✓ | ✓ | ✗ | ✗ |
| Geometric canvas | ✓ | ✓ | ✓ | ✓ |

### Test Suite

The `almaqlub-tests.html` file contains 40+ automated tests organized in 8 groups:

1. **Core Functions** — stripForCompare, isLetterPalindrome, isWordPalindrome, symmetryScore
2. **UI Structure** — DOM elements, navigation, RTL, fonts, Bismillah
3. **Library** — poem data integrity, card rendering, type coverage, specific poems
4. **Creator** — input, keyboard, analysis panel, mic button, save/export
5. **Game** — difficulty controls, puzzle generation, scoring, input
6. **Reciter** — select, display, waveform, speed slider, controls
7. **Accessibility & Design** — CSS variables, fonts, dark theme, particles
8. **Edge Cases** — single characters, empty strings, long strings, navigation

Open `almaqlub-tests.html` in the same directory as `almaqlub.html` and click "Run All Tests".

---

## Files

| File | Description |
|------|-------------|
| `almaqlub.html` | Full application (single file, ~65KB) |
| `almaqlub-tests.html` | Automated test suite (40+ tests, iframe-based) |
| `README.md` | This documentation |
| `README.html` | Interactive help page (same content, styled) |
| `CHANGELOG.md` | Version history |

---

## License

Part of the كلامي (Kalami) Arabic tools project.

---

بارك الله فيك 🌙
