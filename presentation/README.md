# Hamid Rather Introduction Presentation

This directory contains a reproducible generator for Hamid Rather's introduction deck.

## Files

- `create_presentation.py` - builds the presentation from repository source data.
- `hamid_rather_introduction.pptx` - generated deck for sharing.

## Source of truth

The script reads:

- `/_config.yml`
- `/_data/careers.yml`
- `/_data/education.yml`
- `/_data/projects.yml`
- `/_data/skills.yml`
- `/_data/contact.yml`

## Regenerate

From repository root:

```bash
python -m pip install python-pptx PyYAML
python presentation/create_presentation.py
```

The output is written to:

`presentation/hamid_rather_introduction.pptx`
