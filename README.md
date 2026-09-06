# shared-tags

Shared controlled vocabulary for course metadata, used across the veltzer
teaching projects (`teaching-syllabi`, `teaching-slides`,
`business-syllabi`). Like `shared-terms` and `shared-themes`, it is
consumed as a git submodule mounted at `shared/shared-tags/`.

## What this is

Each `.txt` file is the closed set of values one syllabus front-matter
field may take. `rsconstruct`'s `tags` processor validates every syllabus
against these lists, so a typo or an invented category fails the build
instead of quietly producing an unfindable course.

This is a *vocabulary*, not a dictionary of prose terms -- that is
`shared-terms`, which checks how technology names are written in running
text. The two are unrelated and are consumed by different processors.

## Layout

One file per field, one value per line, sorted:

- `level.txt`, `category.txt`, `audiences.txt` -- the core classification
- `duration_hours*.txt` -- permitted course lengths
- `languages.txt`, `tools.txt`, `concepts.txt`, `practices.txt` -- subject tags
- the remainder (`databases`, `networking`, `security`, ...) -- topic areas

## Editing

Add a value here first, then use it in a syllabus. A value that no
syllabus uses is harmless; a syllabus using a value absent from these
lists fails the build in every consuming repo.

Keep each file sorted and free of duplicates, so a diff shows what
actually changed.
