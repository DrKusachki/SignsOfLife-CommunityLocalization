# Updating a translation after an English refresh

Check the target version in the [README](README.md) against the game's main
menu. Keep editing the files in `locales/<code>/Config/`. The
[English reference](english/Config/) is the source for wording and IDs.

## Updating from 1.1.1 to 1.1.5

Start with the Workbench crafting labels and the new AGIS tutorial prompts.
Review **Manual Hotbar Radial Type** and **Agis Notifications** in Settings.
The [English change report](changes.md) also
lists the new item, Codex, and crafting category text.

## Read the change report

Open [the English changes](changes.md), then find your language in
[Translation review status](translation-review.md). Use the table, ID, and
field to locate an entry. Recipe and armor entries also have a section, and
runtime-content entries have a kind.

| Status | What to do |
| --- | --- |
| Added | Translate the new field when you are ready to cover it. |
| Changed | Compare the old and new English. Update your translation where needed. |
| Replaced | Review the destination's English and tokens before reusing any old wording. Check for an existing translation at that destination. |
| Unused | Remove the obsolete field. Remove the row only after checking its other fields. |
| Removed | Ask a maintainer what happened to the field before deleting it. |

Keep lookup IDs and tokens intact, including placeholders such as `{0}` and
controls such as `[equipkey]`. Reports leave your locale files as they are.
For earlier snapshots, find the relevant report in the history of
[`changes.md`](changes.md). Outstanding reviews carry forward.

## Recipes that share their result's name

If the English recipe has `DisplaySource`, translate the name of the referenced
item, block, or object in its own file. For a recipe you previously named
separately, copy the English `DisplaySource` into the matching locale recipe
row and remove that row's `DisplayName` to use the shared name. Keep the locale
`DisplayName` if the recipe needs its own wording.

## Acknowledge reviewed wording

1. If the translation still fits the current English, use the
   `acknowledgment` object for that field in
   [`translation-review.json`](translation-review.json), under your language's
   `needsReview` list.
2. If you edited the translation, push the edit to your translation PR first.
   Open **Checks → Translation review**, download the `translation-review`
   artifact from the run, and use the acknowledgment in its JSON report.
3. Copy the whole object to the `reviewed` array in
   `locales/<code>/review-state.json`. If that same field already has a record,
   replace it. Include the review-state file in your translation PR.

Test your locale pack in the game. If it fails to load, fix the reported JSON
error and retry **Load Now**. See [Translating Signs of Life](TRANSLATING.md)
for table-specific instructions.
