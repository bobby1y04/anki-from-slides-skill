# Anki from Slides 📚

Turn lecture PDFs into a manageable set of Anki cards, with a source on every card and slide screenshots where they help.

The skill is called `anki-aus-folien`. Its instructions are in German, but the cards follow the language of the source slides unless you ask for a different language.

## Getting started

You'll need an AI assistant that supports `SKILL.md` skills and can read PDFs. For the full output, it also needs tools to render pages, crop images, create files and provide downloads.

1. Add the `anki-aus-folien` folder using your application's skill setup. Follow its documentation for the correct location or import method.
2. Enable or select the skill, then upload the PDFs you want to use.
3. Ask for cards. For example:

> Use anki-aus-folien with the attached lecture PDF. Create a focused set of question-and-answer cards with sources, and include a separate ZIP of useful slide screenshots.

This repository contains instructions and metadata, with no installer. Downloading it alone doesn't activate the skill.

Keep the original PDF filenames so the source references are easy to follow. The assistant should only use the PDFs selected for the current request. You can also ask for no images, screenshot suggestions only, or a chat-only answer.

## What you get

### Anki cards

A UTF-8 TSV file with two fields per note:

- **Front:** the question.
- **Back:** the answer and its source.

The aim is to cover the main concepts without turning every bullet point into a card. Each card has one focused learning point. There are no cloze deletions or automatic reverse cards.

Sources include the original PDF filename, physical PDF page and a specific location on the page. A different printed slide number is listed separately. The assistant should use only the supplied material and ask about unclear passages or leave out uncertain cards.

Separate modules get separate files. The cards use Anki's Basic note type and MathJax for formulas. You choose the destination deck.

### Slide screenshots 🖼️

When an image helps explain a card, a separate ZIP contains PNG crops from the original slides and a `Zuordnung.txt` file. “Zuordnung” means “mapping”: this file links each image to the exact question, card file and source, and explains how to add it.

The assistant should check every crop against the original, keeping the necessary labels, axes and legends. There is no image quota and no empty ZIP if nothing useful can be cropped.

Unzip the package, find the card by its question text, and add the PNG manually in Anki Desktop, usually to the back. **Importing the TSV does not import the images.**

If the environment can't create the images, the assistant should explain the limitation and still deliver the checked cards. Visually checked screenshot suggestions can serve as a fallback. A chat-only request gets no ZIP unless you ask for one as well.

## Importing into Anki

1. Import the TSV in Anki Desktop.
2. Select your deck and the Basic note type.
3. Map column 1 to Front and column 2 to Back.
4. Check the preview, tab separator and HTML setting before importing.

The headers `#separator:Tab` and `#html:true` are supported by Anki 2.1.54 and later. Older versions may need those settings entered manually.

To add new notes without changing existing ones, choose the option to ignore existing notes. Anki checks duplicates using the first field within the selected matching scope, so rewording a question can create a new note on a later import.

The skill doesn't import cards itself or change existing decks, templates or study limits unless you ask.

See Anki's documentation for [text imports](https://docs.ankiweb.net/manual/importing/text-files) and [MathJax](https://docs.ankiweb.net/manual/math).

## Checking the results

The skill requires at least two separate passes: first create the cards, then check every card against the original PDF for accuracy, the requested format and learning value. Changed or added cards must be checked again. The TSV, screenshots and image mapping also get file checks.

The assistant can still make mistakes. Use the source references to check important details yourself. The full workflow is in [SKILL.md](anki-aus-folien/SKILL.md).

## Privacy and course material

This package contains no lecture PDFs, personal information or sample decks, and requires no credentials stored in the repository. Your AI application determines how uploaded PDFs are processed and stored. The skill does not guarantee local-only processing.

Only upload material you're allowed to use in that environment, and check it for personal or confidential information first. Cards, screenshots and mappings can carry over source content and filenames, so review them before sharing.

Sharing this skill doesn't give you permission to publish someone else's slides, figures or derived cards. Check copyright, course rules and usage terms before putting course material in a public repository.

## Files

- `README.md`: this guide.
- `anki-aus-folien/SKILL.md`: the workflow and checking rules.
- `anki-aus-folien/agents/openai.yaml`: display metadata and a default prompt.

## License

No license has been chosen yet. Public availability alone does not grant a license to reuse the material.
