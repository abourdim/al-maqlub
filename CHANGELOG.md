# Changelog

All notable changes to المقلوب · Al-Maqlub are documented in this file.

---

## v1.0.0 — 2026-03-07

### المقلوب · Al-Maqlub — Arabic Reversible Poetry

Initial public release. Single-file browser application for exploring, creating, playing with, and reciting Arabic palindrome poetry.

### Added

#### Library (المكتبة)
- 10 verified classical Arabic palindrome verses covering 4 types: letter (المقلوب الحرفي), word/crab (السرطاني), sentence (المستوي), half-verse mirror (شطر مقلوب)
- Decorated cards with Amiri calligraphic text, type badges, EN/FR translations, century/source attribution
- Symmetry axis animation: gold vertical center line with mirror pairs illuminating gold (match) or crimson (mismatch) from center outward
- Forward/backward text toggle with smooth animation
- Text-to-speech playback (ar-SA via Web Speech API)

#### Creator (المحرر)
- Arabic text input area (RTL, Amiri font, large display)
- Full Arabic virtual keyboard: 28 letters, Arabic numerals (٠–٩), punctuation (،؟!.), backspace, word-delete, space bar
- Microphone dictation via Web Speech API (ar-SA, continuous recognition, Chrome/Edge)
- Real-time analysis: letter palindrome check (✓/✗), word palindrome check (✓/✗), symmetry score 0–100% with animated SVG arc
- Color-coded letter map: gold = matching mirror pair, crimson = mismatch
- Fix suggestions panel showing mismatched positions
- Save to session collection (sessionStorage)
- Export as decorative SVG card (dark background, gold border, symmetry score)

#### Game (اللعبة)
- 3 difficulty levels: حروف (fill 1–3 letters, 10pts), كلمات (fill missing words, 25pts), بيت (reconstruct mirror half, 50pts)
- Puzzles randomly generated from Library collection
- Arabic virtual keyboard for input
- Instant visual feedback: gold glow + particle burst (correct), crimson shake (wrong) with correct answer shown
- Score counter + consecutive streak badge
- Optional 30-second timer mode per puzzle

#### Reciter (المنشد)
- Library poem selector dropdown + custom text paste area
- 3 playback modes: forward (gold highlights), backward (crimson highlights), dual (forward → 500ms pause → backward)
- Speed slider 0.5× to 2× (affects speech rate + highlight timing)
- Animated waveform bars synchronized to playback state
- Letter-by-letter highlight timing estimated from character count and speech rate

#### Design System
- كلامي (Kalami) family design language: dark void (#030508) background, gold (#c8922a) accents, teal (#1a9f88) success, crimson (#c0392b) error
- Typography: Amiri (Arabic display), Cinzel (UI headers), DM Mono (data/badges)
- بِسْمِ اللَّهِ الرَّحْمَنِ الرَّحِيمِ golden glowing header with pulse animation
- Animated Islamic geometric canvas background (8-point stars + rosettes, 12% opacity)
- Coloured mosaic tile border (gold/teal/crimson repeating bands, 5px)
- Cards: dark surface + gold border + hover lift + top-edge gold gradient line
- Particle burst system for game celebrations
- Responsive layout with 600px breakpoint

#### Core Engine
- `stripForCompare()`: removes tashkeel (0610–061A, 064B–065F, 0670, 06D6–06DC), tatweel (0640), whitespace, punctuation (،؟!,.?), normalizes alef variants (إأآ → ا) and hamza carriers (ؤئ → ء)
- `isLetterPalindrome()`: strip then reverse-compare character sequence
- `isWordPalindrome()`: strip each word then reverse-compare word order
- `symmetryScore()`: percentage of matching mirror-position letter pairs

#### Documentation
- `README.md`: comprehensive project documentation with features, how-to, FAQ, troubleshooting, technical reference
- `README.html`: interactive styled help page matching app design, with collapsible FAQ, step-by-step guides, troubleshooting cards
- `CHANGELOG.md`: this file
- `almaqlub-tests.html`: automated test suite — 40+ tests in 8 groups (core functions, UI structure, library, creator, game, reciter, accessibility, edge cases)

### Technical Notes
- All 10 library poems verified against palindrome functions with passing tests
- Alef/hamza normalization added to ensure consistent comparison across variant forms
- Word palindrome comparison strips each word individually before comparing order
- Single HTML file, ~65KB, zero external dependencies (except Google Fonts CDN)
- Works offline for all features except font loading and TTS
