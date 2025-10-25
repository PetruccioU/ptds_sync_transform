# ptds_sync_transform

# 🎨 Tokens Studio – GitHub Sync Test

This repository is used to test and document how **Tokens Studio for Figma** integrates with **GitHub** using **push** and **pull** operations for design tokens.

---

## 🧩 Overview

This project explores how Tokens Studio manages and synchronizes design tokens (e.g., color, typography, spacing, etc.) between **Figma** and a **GitHub repository**.

By linking this repo to Tokens Studio, we can:
- **Push** tokens from Figma → GitHub (save design token updates)
- **Pull** tokens from GitHub → Figma (load and apply saved tokens)

---

## 📁 Repository Structure

├── tokens/
│ ├── global.json
│ ├── light.json
│ ├── dark.json
│ └── README.md
├── .github/
│ └── workflows/ (optional CI/CD)
├── .gitignore
└── README.md


> You can adjust the folder and file naming convention based on your token setup (single file or multi-theme structure).

---

## ⚙️ Setup Instructions

### 1. Connect Tokens Studio to GitHub
1. In **Figma**, open **Tokens Studio** plugin.
2. Go to **Sync → GitHub Sync**.
3. Click **Connect Repository** and authenticate with GitHub.
4. Choose this repository (`<your-username>/<repo-name>`).
5. Select the folder where tokens will be stored (e.g., `/tokens`).

---

## 🔄 Push & Pull Workflow

### ▶️ **Push (Figma → GitHub)**
Use this option when you want to **save updated tokens** from Figma into the GitHub repository.

- In Tokens Studio:  
  `Sync → Push changes → Select branch → Confirm`
- The updated token files (JSON) will be committed automatically.
- Commit message example:


### ⬅️ **Pull (GitHub → Figma)**
Use this option when you want to **load tokens** from GitHub into your Figma project.

- In Tokens Studio:  
`Sync → Pull changes → Select branch → Confirm`
- Tokens will update in your Figma file to match the repository version.

---

## 🧠 Tips & Best Practices

- Always **pull before pushing** to avoid overwriting others’ changes.
- Use **branching** (`feature/tokens-update`) for collaborative token changes.
- Keep commit messages descriptive (e.g., `feat(tokens): add new semantic colors`).
- Consider using **GitHub Actions** to validate token files (e.g., JSON linting).

---

## 💾 Example Token JSON

Below is the exported token structure from **Tokens Studio** used for testing.

```json
{
"dimension": {
  "scale": { "$type": "dimension", "$value": "2" },
  "xs": { "$type": "dimension", "$value": "4" },
  "sm": { "$type": "dimension", "$value": "{dimension.xs} * {dimension.scale}" },
  "md": { "$type": "dimension", "$value": "{dimension.sm} * {dimension.scale}" },
  "lg": { "$type": "dimension", "$value": "{dimension.md} * {dimension.scale}" },
  "xl": { "$type": "dimension", "$value": "{dimension.lg} * {dimension.scale}" }
},
"spacing": {
  "xs": { "$type": "spacing", "$value": "{dimension.xs}" },
  "sm": { "$type": "spacing", "$value": "{dimension.sm}" },
  "md": { "$type": "spacing", "$value": "{dimension.md}" },
  "lg": { "$type": "spacing", "$value": "{dimension.lg}" },
  "xl": { "$type": "spacing", "$value": "{dimension.xl}" },
  "multi-value": {
    "$type": "spacing",
    "$value": "{dimension.sm} {dimension.xl}",
    "$description": "You can have multiple values in a single spacing token. Read more: https://docs.tokens.studio/available-tokens/spacing-tokens#multi-value-spacing-tokens"
  }
},
"borderRadius": {
  "sm": { "$type": "borderRadius", "$value": "4" },
  "lg": { "$type": "borderRadius", "$value": "8" },
  "xl": { "$type": "borderRadius", "$value": "16" },
  "multi-value": {
    "$type": "borderRadius",
    "$value": "{borderRadius.sm} {borderRadius.lg}",
    "$description": "Multiple values supported. https://docs.tokens.studio/available-tokens/border-radius-tokens#single--multiple-values"
  }
},
"colors": {
  "black": { "$type": "color", "$value": "#000000" },
  "white": { "$type": "color", "$value": "#ffffff" },
  "gray": { ... },
  "red": { ... },
  "orange": { ... },
  "yellow": { ... },
  "green": { ... },
  "teal": { ... },
  "blue": { ... },
  "indigo": { ... },
  "purple": { ... },
  "pink": { ... }
},
"opacity": {
  "low": { "$type": "opacity", "$value": "10%" },
  "md": { "$type": "opacity", "$value": "50%" },
  "high": { "$type": "opacity", "$value": "90%" }
},
"fontFamilies": {
  "heading": { "$type": "fontFamilies", "$value": "Inter" },
  "body": { "$type": "fontFamilies", "$value": "Roboto" }
},
"lineHeights": {
  "heading": { "$type": "lineHeights", "$value": "110%" },
  "body": { "$type": "lineHeights", "$value": "140%" }
},
"letterSpacing": {
  "default": { "$type": "letterSpacing", "$value": "0" },
  "increased": { "$type": "letterSpacing", "$value": "150%" },
  "decreased": { "$type": "letterSpacing", "$value": "-5%" }
},
"paragraphSpacing": {
  "h1": { "$type": "paragraphSpacing", "$value": "32" },
  "h2": { "$type": "paragraphSpacing", "$value": "26" }
},
"fontWeights": {
  "headingRegular": { "$type": "fontWeights", "$value": "Regular" },
  "headingBold": { "$type": "fontWeights", "$value": "Bold" },
  "bodyRegular": { "$type": "fontWeights", "$value": "Regular" },
  "bodyBold": { "$type": "fontWeights", "$value": "Bold" }
},
"fontSizes": {
  "h1": { "$type": "fontSizes", "$value": "roundTo({fontSizes.body}*1.25^5)" },
  "h2": { "$type": "fontSizes", "$value": "roundTo({fontSizes.body}*1.25^4)" },
  "h3": { "$type": "fontSizes", "$value": "roundTo({fontSizes.body}*1.25^3)" },
  "h4": { "$type": "fontSizes", "$value": "roundTo({fontSizes.body}*1.25^2)" },
  "h5": { "$type": "fontSizes", "$value": "roundTo({fontSizes.body}*1.25^1)" },
  "h6": { "$type": "fontSizes", "$value": "{fontSizes.body}" },
  "body": { "$type": "fontSizes", "$value": "16" },
  "sm": { "$type": "fontSizes", "$value": "{fontSizes.body} * 0.85" },
  "xs": { "$type": "fontSizes", "$value": "{fontSizes.body} * 0.65" }
}
}

