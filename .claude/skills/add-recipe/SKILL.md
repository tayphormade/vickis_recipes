---
name: add-recipe
description: Convert a recipe from a PDF, DOCX, image, web page, or pasted text into this repo's Markdown format and add it to the README index. Use when adding a new recipe, or when reformatting or correcting an existing one.
---

# Add a recipe

Use `soups/panera-chicken-wild-rice-soup.md` as the reference example.

## 1. Extract the recipe accurately

Accuracy matters more than formatting. A wrong quantity can ruin a dish, so check every value against the original.

- **PDF:** Run `pdftotext`, then also render the pages with `pdftoppm` and read the images. Text extraction can silently drop fractions, digits, and words. For example, "½ cup" can become "1 cup" and "10–12 minutes" can become "0–2 minutes". The rendered page is the source of truth.
- **Scanned PDF or image:** Read the rendered image directly. Use OCR only as a starting point, because it garbles fractions.
- **DOCX:** Convert with `pandoc -t gfm`, then unzip the file and look at everything in `word/media/`. Photos and screenshots may contain the actual ingredients and steps.
- **Unreadable values:** Don't guess. Ask the user, or mark the value as unknown in the notes.

## 2. Choose the location and name

- Put the recipe in a lowercase, plural category folder such as `soups/`. Create a new folder only if no existing category fits.
- Name the file in kebab-case after the dish, such as `panera-chicken-wild-rice-soup.md`.
- Leave website and brand names out of new titles and filenames. Credit the source in the source line and notes instead.

## 3. Write the file

Follow this structure and leave out any line that doesn't apply:

```markdown
---
title: "Recipe Name"
source_url: "https://example.com/exact-recipe-page"
---

# Recipe Name

🔗 **Source:** [Site Name](https://example.com/exact-recipe-page)

- 🍽️ **Servings:** 4
- ⏱️ **Prep:** 15 minutes
- ⏲️ **Cook:** 30 minutes

---

## 🛒 Ingredients

### 🍗 Component

- 🐔 1 lb chicken breast

### 🥣 Other Component

- 🥦 **Group**
  - 🥕 1 cup sliced carrots

---

## 👩‍🍳 Steps

1. 🔪 Slice the carrots.
2. 🔥 Bring the soup to a boil.

---

## 📝 Notes

- 🌟 A tip, variation, or substitution.

*Attribution or copyright line, if the source has one.*
```

### Source

- Link to the exact recipe page, not a category page or home page.
- If the source file has no URL, you may search for one. Add it only if the title and content clearly match.
- If no source can be confirmed, omit both `source_url` and the source line. Don't write "unknown" or "none found".

### Top section

- Include only servings, timing, and short facts such as calories or dietary labels.
- Omit values the source doesn't give. Don't write "not listed".
- If you calculate a time, show the math and include every part: `about 70 minutes (10 + 20 + 30 + 10 minutes)`.
- Move descriptions and commentary to the notes.

### Ingredients

- Use a `###` heading for each distinct component when the recipe has them, such as Chicken and Soup.
- Group related items with a bold bullet and sub-bullets, such as vegetables, broth, or herbs and spices. Every ingredient is a bullet or sub-bullet.
- If the recipe depends on order, such as jar layering, keep the original order.
- List optional ingredients as optional, and include any that appear only in the steps.

### Steps

- Use one flat numbered list with one main action per step. Don't use substeps or section headings, and don't bold the step text.
- Start every step with an emoji.
- If a recipe has several cooking methods, give each method a `###` heading and its own numbered list.
- Keep every detail when splitting or rewording steps, especially refrigeration, food safety, temperatures, times, and "save this for later" instructions.
- Mark optional ingredients with "if using" in the steps.
- "Enjoy!" is not a step.

### Notes

- Use a bulleted list with an emoji on every bullet.
- Keep tips, substitutions, variations, allergens, equipment, and warnings. Cut filler and marketing copy.
- Make sure step references match the final step numbers, and that each note refers to the correct ingredient or amount.

### Emojis

- Put an emoji on every ingredient, group, step, and note.
- Within a recipe, use each emoji for only one thing. The same ingredient can keep its emoji wherever it appears.

## 4. Keep it safe to publish

This repo is public.

- Never include local file paths, usernames, or machine details.
- Don't refer to files readers can't open, such as "the original PDF" or "the .docx".
- Add only the Markdown. Don't add the original PDFs, DOCX files, or images.

## 5. Update the README

Add a bullet under the category's `##` heading in `README.md`, creating the heading if needed. Use one emoji that fits the dish, and link to the file:

```markdown
- 🥣 [Recipe Name](soups/recipe-name.md)
```

## 6. Check your work

- [ ] Every quantity, time, and temperature matches the rendered original.
- [ ] Nothing important was dropped, especially warnings and storage steps.
- [ ] Step references in the notes are correct.
- [ ] Every emoji rule is met, and step text isn't bold.
- [ ] The README link points to a file that exists.
- [ ] A search for local paths and `.pdf` or `.docx` mentions finds nothing.

## 7. Commit and push only when asked

- Commit only when the user asks.
- Never push unless the user explicitly says to in that moment. Earlier permission doesn't carry over.
- Never force push without explicit permission.
- Tell the user about anything you couldn't verify or had to interpret.
