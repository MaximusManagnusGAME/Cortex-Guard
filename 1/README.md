# CortexGuard-1-En

**Version:** 1  
**Language:** English only

CortexGuard-1-En is a browser-based English profanity filtering engine designed to resist common text-filter evasion techniques.

## Repository layout

This file belongs to the `1/` directory of the main **CortexGuard** repository.

```text
CortexGuard/
├── .gitignore
├── 1/
│   ├── index.html
│   └── README.md
├── 1.1/
├── 1.2/
└── ...
```

Each future release can live in its own version directory without changing the repository name.

## Main capabilities

- Unicode NFKD normalization
- Combining-mark removal
- Zero-width, control and bidirectional-format character removal
- Greek, Cyrillic and other common cross-script confusable mappings
- Decorative, enclosed, full-width and mathematical alphabet normalization
- Regional-indicator letter handling
- Common leetspeak substitutions
- Masked-character handling
- Repeated-character reduction
- Missing internal character detection
- One or two inserted-character detection depending on term length
- Adjacent character transposition detection
- Selected phonetic and visual rewrite rules
- Escaped Unicode decoding such as `\u0066`
- Hex escape decoding such as `\x66`
- `U+0066` notation decoding
- Numeric HTML character-reference decoding
- Word-level analysis for normal sentences
- Compact analysis for separator-based evasions
- English inflection handling
- Limited fuzzy matching for longer terms
- Built-in false-positive protection for selected ordinary English words
- Automatic internal regression tests
- Responsive desktop, tablet and mobile interface
- Lucide icons only
- No visible test panel

## Files

- `index.html` — complete interface and moderation engine
- `README.md` — documentation
- `.gitignore` — Git ignore rules

## Running the project

No build step is required.

Open `index.html` in a modern browser.

Lucide Icons are loaded from a CDN, so the icons require an internet connection unless the Lucide dependency is later bundled locally.

## JavaScript API

The engine is exposed as:

```js
CortexGuard1En
```

Example:

```js
const result = CortexGuard1En.detectProfanity("b!tch");

console.log(result.blocked);
console.log(result.matched);
console.log(result.rule);
```

Run the internal regression suite:

```js
console.log(CortexGuard1En.runSelfTests());
```

## Production use

Do not rely on browser-side filtering alone.

A user can modify or bypass JavaScript running in their browser. Production systems should apply equivalent validation on the server before saving or publishing user-generated text.

Recommended production steps:

1. Run the moderation engine server-side.
2. Keep the server-side term set authoritative.
3. Apply reasonable input length limits.
4. Add rate limiting to submission endpoints.
5. Log moderation decisions when appropriate.
6. Maintain regression tests for both evasions and false positives.
7. Review the vocabulary and confusable mappings over time.

## Accuracy note

No profanity filter can guarantee detection of every possible future spelling, slang term, Unicode trick or adversarial encoding while also guaranteeing zero false positives.

CortexGuard-1-En intentionally combines several defensive techniques while limiting unrestricted fuzzy matching on short words, because aggressive edit-distance matching can incorrectly classify ordinary words.

## Version

CortexGuard-1-En — Version 1
