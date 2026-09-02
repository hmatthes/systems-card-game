# Maintainer guide: adding adaptations and workshops

This guide explains how to add a documented card-set adaptation and its associated workshops to the Systems Card Game repository.

The GitHub Pages website is built from the files inside the `docs` folder. Files elsewhere in the repository do not normally become website pages.

## 1. Understand the basic structure

Every adaptation has its own folder inside:

```text
docs/applications/
```

A completed adaptation normally has this structure:

```text
docs/applications/adaptation-name/
├── index.md
├── adaptation.md
├── adaptation-image.jpg
├── materials/
│   ├── printable-cards.pdf
│   └── facilitation-guide.pdf
└── workshops/
    └── workshop-name/
        ├── index.md
        ├── report.md
        └── workshop-image.jpg
```

The files have different purposes:

- `index.md` in the adaptation folder is the visual adaptation landing page.
- `adaptation.md` contains the full adaptation documentation.
- `materials` contains downloadable card sets, guidance and related files.
- `index.md` in a workshop folder is the visual workshop landing page.
- `report.md` contains the full workshop documentation.
- Images used on a particular page normally sit in the same folder as that page.

A workshop that uses an existing card-set adaptation should be placed under that adaptation. It does not need a separate adaptation folder.

## 2. Choose folder names

Use a short, descriptive folder name containing:

- lowercase letters;
- hyphens instead of spaces;
- no special characters.

For example:

```text
reindeer-herding
ilulissat-livelihoods
young-people-reindeer-husbandry
```

The folder name does not have to be identical to the title displayed on the website.

In this guide, the following placeholders are used:

```text
ADAPTATION-SLUG
WORKSHOP-SLUG
```

Replace these everywhere with the actual folder names.

## 3. Collect the necessary information

Before creating the pages, collect as much of the following as possible.

### For an adaptation

- Title
- System or topic
- Purpose
- Card categories
- Available languages
- Description of how the general tool was adapted
- List of downloadable materials
- Guidance for reuse
- Developers and contributors
- Translators and translation checkers, where applicable
- Contact person and email address
- References, reports, project pages or DOIs
- Names of workshops or courses using the adaptation
- At least one image, if available
- Image caption and credit
- Permission to publish the image and materials

### For a workshop

- Workshop title
- Adapted card set used
- Date and location
- Organisers and facilitators
- Participants
- Purpose
- Workshop format and duration
- Changes made for the event
- Outcomes and observations
- Follow-up activities
- Available documentation
- Contact person and references
- At least one image, if available
- Image caption and credit
- Permission to publish workshop images and documentation

Missing information can be marked temporarily with an HTML comment:

```html
<!-- Information still needed: number of participants. -->
```

Comments written in this form are visible in the Markdown source but not on the website.

## 4. Create an adaptation folder

In github.dev:

1. Open `docs/applications`.
2. Create a folder using the adaptation slug.
3. Inside it, create:
   - `index.md`
   - `adaptation.md`
   - `materials`
   - `workshops`
4. Upload the adaptation image into the adaptation folder.
5. Upload card sets and other downloadable files into `materials`.

Git does not retain completely empty folders. If `materials` or `workshops` disappears, create a file inside it or wait until material is ready to upload.

## 5. Create the adaptation landing page

The adaptation’s `index.md` is its short, visual landing page.

Begin it with:

```yaml
---
title: DISPLAYED ADAPTATION TITLE
nav_order: NUMBER
parent: Adaptations and workshops
permalink: /applications/ADAPTATION-SLUG/
---
```

Important:

- `title` controls the title used by Jekyll and the navigation system.
- `nav_order` controls the adaptation’s position among the other adaptations.
- `parent` must be exactly `Adaptations and workshops`.
- `permalink` determines the final website address.
- Keep the leading and trailing `/` in the permalink.

A typical adaptation landing page contains:

1. Page title
2. Short introduction
3. Adaptation image
4. Brief “About this adaptation” section
5. Button linking to the full adaptation documentation
6. Table of downloadable materials
7. Optional video or other media
8. Visual teasers for workshops using the adaptation

### Linking to the full documentation

Use the website permalink rather than linking to `adaptation.md` directly:

```markdown
[Read the full adaptation documentation]({{ site.baseurl }}/applications/ADAPTATION-SLUG/adaptation/){: .btn .btn-primary }
```

### Displaying an adaptation image

```html
<p align="center">
  <img src="adaptation-image.jpg"
       alt="A meaningful description of the image"
       style="width: 100%; max-width: 620px; height: auto;">
  <br>
  <small>Image caption and credit.</small>
</p>
```

The `alt` text should describe the image for people using screen readers. It is not the same as the visible caption or image credit.

### Linking downloadable material

When the material is in the adaptation’s `materials` folder, use:

```markdown
[Download the English card set](materials/english-card-set.pdf)
```

A table is useful when the same material is available in several languages:

```markdown
| Language | Printable card set |
|---|---|
| English | [Download](materials/english-card-set.pdf) |
| Kalaallisut | [Download](materials/kalaallisut-card-set.pdf) |
```

## 6. Create the full adaptation documentation

Begin `adaptation.md` with:

```yaml
---
title: DISPLAYED ADAPTATION TITLE full documentation
nav_exclude: true
permalink: /applications/ADAPTATION-SLUG/adaptation/
---
```

`nav_exclude: true` keeps the documentation page out of the navigation bar while allowing it to be published and linked from the adaptation landing page.

The documentation should normally contain:

```markdown
# Title of the adaptation* 
[*a title, if you have one, or a short name for the system*]

[Back to the adaptation overview]({{ site.baseurl }}/applications/ADAPTATION-SLUG/)

## System or topic* 
[*what system or topic was the tool adapted to?*]

## Purpose* 
[*for what purpose did you make the tool? what discussion or decisions was the tool meant to support?*]

## Card categories
[*if you specified the general card categories into categories more specific to your system, you can list and describe them here*]

## Languages
[*in which languages are the cards available?*]

## How the general tool was adapted 
[*you can describe your adaptation process here*]

## Available materials
[*please list the material you would like to make available through the repository*]

## Guidance for reuse
[*If there is guidance for using the adapted cards, you can add it here. If you have a sperate document, please provide it with your documentation and simply put the name here. We will link it here. If you used general guidance, please indicate that here.*]

## Development and contributors* 
[*who developed the adaptation?*]

## Contact* and references
[*Please give the name and email of a contact person for your adaptation. if there are publications associated with your adaptation, you can provide them here.*]

## Workshops or courses using the adaptation
[*if you have used the adaptation, you can provide information here. you can also list the documented workshops/courses you put into the repository*]
```

Remove sections that genuinely do not apply. Use comments for information that is expected but not yet available.

## 7. If you want the adaptation to have a teaser

All adaptations with:

```yaml
parent: Adaptations and workshops
```

are automatically included in the adaptation list generated by Just the Docs.

A separate manual list of all adaptations is therefore not necessary.

Only selected adaptations need a visual teaser on:

```text
docs/applications/index.md
```

If the new adaptation should be featured there, copy an existing teaser and change:

- the title;
- the description;
- the image;
- the image’s `alt` text;
- the link to the adaptation.

## 8. Create a workshop folder

Inside the adaptation folder, go to:

```text
workshops/
```

Create a new folder using the workshop slug:

```text
docs/applications/ADAPTATION-SLUG/workshops/WORKSHOP-SLUG/
```

Inside it, create:

```text
index.md
report.md
```

Upload workshop photographs or images into the same folder.

A workshop folder may contain several images:

```text
initial-map.jpg
critical-points.jpg
disruption-cards.jpg
```

Use descriptive lowercase filenames with hyphens. Avoid spaces where possible.

## 9. Create the workshop landing page

Begin the workshop `index.md` with:

```yaml
---
title: DISPLAYED WORKSHOP TITLE
nav_exclude: true
permalink: /applications/ADAPTATION-SLUG/workshops/WORKSHOP-SLUG/
---
```

The workshop landing page normally contains:

1. Workshop title
2. Link back to the adaptation
3. Workshop image or image sequence
4. Short summary
5. Workshop information table
6. Button linking to the full report
7. Links to external reports or downloadable outputs, if available

### Back link to the adaptation

```markdown
[Back to the adaptation title]({{ site.baseurl }}/applications/ADAPTATION-SLUG/)
```

### Workshop information table

```markdown
| Workshop information | |
|---|---|
| **Date** | DATE |
| **Location** | LOCATION |
| **Context** | EVENT OR PROJECT |
| **Duration** | DURATION |
| **Participants** | PARTICIPANT SUMMARY |
| **Format** | WORKSHOP FORMAT |
| **Language** | LANGUAGE |
```

Rows without useful information can be omitted until the information becomes available.

### Link to the full report

Use the report’s final permalink:

```markdown
[Read the full workshop documentation]({{ site.baseurl }}/applications/ADAPTATION-SLUG/workshops/WORKSHOP-SLUG/report/){: .btn .btn-primary }
```

Do not link to `report.md` when the report has a separate permalink ending in `/report/`.

## 10. Create the full workshop report

Begin `report.md` with:

```yaml
---
title: DISPLAYED WORKSHOP TITLE full workshop report
nav_exclude: true
permalink: /applications/ADAPTATION-SLUG/workshops/WORKSHOP-SLUG/report/
---
```

Do not add `published: false`.

A normal report contains:

```markdown
# Title of the workshop or course* 
[*a title, if you have one, or a short name for the workshop/course*]

[Back to the workshop overview]({{ site.baseurl }}/applications/ADAPTATION-SLUG/workshops/WORKSHOP-SLUG/)

## Adapted card set used* 
[*which card set was used for this activity?*]

## Date and location* 
[*where and when did the workshop/course take place*]

## Organisers* and facilitators 
[*where and when did the workshop/course take place*]

## Participants* 
[*who were the participants? How did they know about the workshop/course? Generalize information as needed, please do not provide personal information*] 

## Purpose* 
[*what purpose was the workshop/course meant to for? what discussion or decisions was the activity meant to support?*]

## Workshop format and duration
[*how was the activity set up? How long did it go on?*]

## Changes made for this particular event/Lessons for future use 
[*Did you adapt the tools, workflow, set up in any way? If you did a similar activity again, what would you do differently?*]

## Outcomes and observations
[*What were the outcomes of the workshop?*]

## Follow-up and potential future use
[*Do you have plans to do similar workshops/courses in the future? What did you do with the results of your activity?*]

## Available documentation
[*If you made a documentation of the workshop/course, you can provide it and we will link it here. Please provide the file name.*]

## Contact* and references 
[*Please give the name and email of a contact person for your adaptation. if there are publications associated with your adaptation, you can provide them here.*]
```

### Link back to the card-set documentation

```markdown
[Read the card-set documentation]({{ site.baseurl }}/applications/ADAPTATION-SLUG/adaptation/)
```

## 11. Add the workshop teaser to the adaptation page

Workshops do not appear automatically on the adaptation landing page.

Open:

```text
docs/applications/ADAPTATION-SLUG/index.md
```

Under `Workshops using this adaptation`, add a teaser linking to the workshop landing page.

A typical teaser is:

```html
| Workshop | Preview |
|---|---|
| **[WORKSHOP TITLE](workshops/WORKSHOP-SLUG/)**<br><br>SHORT DESCRIPTION OF THE WORKSHOP. | <a href="workshops/WORKSHOP-SLUG/"><img src="workshops/WORKSHOP-SLUG/workshop-image.jpg" alt="Meaningful description of the workshop image" width="260"></a> |
```

Check that both links contain:

```text
workshops/WORKSHOP-SLUG/
```

Also replace the copied image `alt` text. It is easy to accidentally leave the description from an earlier workshop in place.

If no image is available yet, use a normal text link temporarily rather than creating an empty teaser table.

## 12. Rules for links

### Links to website pages

Use `site.baseurl` and the page’s permalink:

```markdown
[Link text]({{ site.baseurl }}/applications/ADAPTATION-SLUG/)
```

This is particularly important because the GitHub Pages site is hosted below:

```text
/systems-card-game/
```

### Links to files in the same folder

Use the filename:

```markdown
[Download](file.pdf)
```

### Links to files in a subfolder

Use the relative path:

```markdown
[Download](materials/file.pdf)
```

### External links

Use the full URL:

```markdown
[View the archived material on Zenodo](https://doi.org/10.xxxx/zenodo.xxxxx)
```