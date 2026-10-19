# Signature Bench

A single-file HTML email signature generator. Fill in your details and the preview updates as you type, then copy the signature into your mail app or save it as an HTML file or a vCard contact card.

No install, no build step, no account. Open `signature-bench.html` in a browser and start typing.

## Features

- **Live preview** inside a sample email, with a dark-background view to check your logo stays visible in dark mode
- **Logo** from an uploaded image (embedded in the signature) or a hosted image URL, with alt text and a width slider
- **Flexible contact lines**: add as many as you need, pick a type for each from a dropdown, edit its label, and reorder or remove lines. Types include email, office and mobile phone, fax, website, LinkedIn, other profile links, address, custom text, and a disclaimer/footer. Empty lines are left out.
- **Style options**: logo beside or above the text (or text only), email-safe fonts, text size, text and link colours, labels, divider line, link underlines
- **Accessibility check** that updates as you edit: logo alt text, colour contrast against WCAG AA (4.5:1), links distinguishable from text, text size, and links that won't work
- **Export**
  - Copy the signature as formatted text, ready to paste
  - Copy the raw HTML
  - Save as `.html` (for Thunderbird's "signature from a file")
  - Save as `.vcf` (vCard 3.0), optionally with your logo as the contact photo
- **Remembers your entries** in your browser between visits

## Usage

1. Download `signature-bench.html` and open it in any modern browser.
2. Replace the sample details with your own (or click **Clear form** to start from blank).
3. Choose an export option and follow the steps for your mail app below.

## Installing your signature

| Mail app | Steps |
| --- | --- |
| **Apple Mail** | Click **Copy signature**. In Mail, open Settings → Signatures, click **+**, untick "Always match my default message font", then paste into the right-hand pane. |
| **Thunderbird** | Click **Save .html** and keep the file somewhere permanent. In Account Settings, tick "Use HTML" and "Attach the signature from a file instead", then choose the file. If you move the file later, choose it again. |
| **Gmail** | Switch the logo to **Hosted URL** first. Copy the signature and paste it into Settings → See all settings → General → Signature. |
| **Outlook** | Switch the logo to **Hosted URL** first. Paste into Settings → Mail → Signatures (web/new Outlook) or File → Options → Mail → Signatures (desktop). |

### Embedded vs hosted logos

| | Embedded (uploaded file) | Hosted URL |
| --- | --- | --- |
| Apple Mail | Works | Works |
| Thunderbird | Works | Works |
| Gmail | Removed on paste | Works |
| Outlook | Often blocked | Works |
| What recipients see | Varies by their mail app | Most reliable |

For a hosted logo, upload a PNG somewhere public (your website's media library works well) and paste its full `https://` link.

## How it works

- Signatures are built with tables and inline styles, which is what mail apps render most consistently.
- Uploaded logos are resized in the browser and converted to PNG (or JPEG for photos) to keep the signature small. SVGs are converted too, since most mail apps don't display them.
- Phone numbers become `tel:` links, emails become `mailto:` links, and web addresses get `https://` added if missing.

## Privacy

Everything runs in your browser. Nothing you type or upload is sent anywhere. Your entries are saved in your browser's local storage, on your device only. The only network request is for the interface fonts from Google Fonts. Without a connection it falls back to system fonts and works the same.

## Customising

It's one file of plain HTML, CSS and JavaScript with no dependencies:

- **Sample data**: edit `example()` in the script.
- **Line types**: add an entry to the `TYPES` object (`name`, default `label`, placeholder `ph`, and `kind`: `email`, `tel`, `url`, `plain` or `footer`).
- **Fonts**: add an entry to the `FONTS` object. Stick to fonts installed on most computers, since mail apps can't load web fonts reliably.

## Browser support

Recent versions of Safari, Chrome, Firefox and Edge. If your browser blocks clipboard access, **Copy signature** selects the signature in the preview so you can press ⌘C / Ctrl+C.

## License

[MIT](LICENSE) © 2026 Nevar. Signatures you make with this tool are yours. The license covers the tool itself, not what you create with it.
