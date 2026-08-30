# notebook, tasks & bibliography

## notebook

My notebook is a git repository of hyperlinked markdown files. Hyperlinks use wikilink syntax `[[...]]` and allow linking by filename alone (without the extension) rather than requiring the full path to be provided.

### folder structure

| Folder           | Description                                                                                                         | Target status |
| ---------------- | ------------------------------------------------------------------------------------------------------------------- | ------------- |
| `_assets/`       | for binary assets such as images                                                                                    |               |
| `_templates/`    | for note templates                                                                                                  |               |
| `anki/`          | anki cards in markdown format                                                                                       | `i,s`         |
| `bib/`           | one note per Zotero reference                                                                                       | `i,q,m,r,s,d` |
| `Inbox/`         | receives unprocessed notes                                                                                          |               |
| `Drafts/`        | intended for completion but still a work in progress                                                                |               |
| `Maybe/`         | notes which may be processed further                                                                                |               |
| `Notes/`         | the core note collection, containing subfolders for note types                                                      |               |
| ├─ `zettel/`     | atomic knowledge                                                                                                    |               |
| ├─ `forma/`      | atomic, informational rather than knowledge-based                                                                   |               |
| ├─ `yarn/`       | streams of ideas, not necessarily atomic                                                                            |               |
| ├─ `unknown/`    | open questions                                                                                                      |               |
| ├─ `topic/`      | knowledge-based collection                                                                                          | `i,q,m,r,s`   |
| ├─ `niche/`      | informational collection                                                                                            | `i,q,m,r,s`   |
| ├─ `project/`    | projects work towards a definite end and produce a deliverable                                                      | `i,q,m,w,d`   |
| ├─ `gig/`        | gigs have a definite end, but do not produce a deliverable - for purpose of planning travel, meetings, events, etc. | `i,q,m,d`     |
| ├─ `area/`       | ongoing responsibilities without a definite end                                                                     | `i,q,m,w`     |
| ├─ `experience/` | personal experiences as reference items (meetings, lectures, etc.)                                                  | `i,q,m,d`     |
| └─ `contact/`    | personal contacts and people of interest                                                                            |               |
| `Vault/`         | archived content, mirroring notebook root                                                                           |               |

### note status

_Note status_ is represented by the top-level folders: `Inbox/`, `Drafts/`, `Maybe/`, and `Notes/`.

### note type

_Note types_ correspond to the sub-folders of `Notes/` (`zettel/`, `forma/`, `yarn/`, ...) as well as `anki/` and `bib/`.

Note types can be grouped into the following meta-categories:

| Meta-categories | Included types                                 | Description                                                                                                                                                                                                                                                                   |
| --------------- | ---------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| _knowledge_     | zettel, unknown, topic                         | Knowledge is associated with academic work and other research. Knowledge should distill information and provide understanding. Mere facts, particularly those associated with the organization of my personal life are kept separate.                                         |
| _information_   | forma, niche                                   | Information categories are useful where the purpose is organizational, rather than for the distillation of knowledge. Informational note types are particularly useful for organizing content that is personally relevant, e.g. medication, meal plans, software collections. |
| _atom_          | zettel, forma                                  | Atomic notes capture a single idea. They can stand alone or can they can be reused by linking from various parts of the notebook.                                                                                                                                             |
| _source_        | bib, experience                                | These provide sources to be cited by other notes. A source may be either a bibliographic item stored in Zotero or an experience such as a meeting, lecture or conversation.                                                                                                   |
| _context_       | project, gig, area                             | These provide context to work and tasks. Prefer working within a single context rather than across multiple.                                                                                                                                                                  |
| _collection_    | topic, niche                                   | These are used to organize atomic and source notes related by common themes. General commentary may be included directly in these notes. Exploratory work may operate within a topic or niche rather than a context.                                                          |
| _referent_      | project, gig, area, topic, niche, bib, contact | These refer to external targets. They provide a representation of the target they refer to, even when the note itself contains no content or is incomplete. These notes earn their place in `Notes/` regardless of their state of progress.                                   |

### target status

Some note types refer to a target for which it is useful to have a status that is separate from the primary note status.

The _target status_ is the status of the object which a note refers to, rather than of the note itself.

Target status is represented as a subfolder of the note type folder, e.g. `Notes/project/q` represents queued projects.

Only some note types have a target status. The range of possible values, and the interpretation of the target status, depend on the note type.

The basic set of status values includes:

| Target status | Interpretation |
| ------------- | -------------- |
| `i`           | _inbox_        |
| `q`           | _queued_       |
| `m`           | _maybe_        |
| `d`           | _done_         |

For `bib/`, `topic/`, and `niche/` items, the following status values are also used:

- `r` for _reference_, without intention of being investigated
- `s` for _stable_; partly investigated without intention of consuming further

For `topic/` and `niche/`, the status `d` is omitted since these can never be definitively completed.

Items in `project/` use the basic set, in addition to:

- `w` for _working_, used for projects currently being worked on

Items in `gig/` and `experience/` use the basic set only. There is no practical use to distinguishing between queued and working gigs or experiences, so the working status is omitted.

For `area/`, target status has the same meaning as for `project/`, except that `d` is not available. If an area is no longer being pursued, move it to `Vault` instead.

### operational status

Notes which are not part of `Vault/` are considered _operational_, while `Vault/` provides a location for archiving notes while keeping them searchable.

### context and collection semantics

An area may link to a project or area, which is then considered a _sub-project_ or _sub-area_ of the original area.

Similarly, links from projects to projects are used to represent sub-projects.

The set of areas and projects should be a directed acyclic graph. Unlinked areas and projects may link to the same project or area which is then assumed to exist at the intersection.

A _top-level area_ refers to an area which is not a sub-area of any other area.

A _top-level project_ refers to a project which is not a sub-project of any other project (though it may be a sub-project of an area).

Areas and projects may link to gigs and experiences which are then considered elements of the parent.

A gig is meant to represent travel and events. A link from a gig to an experience indicates that the experience occurred in the context of the gig.

Given a topic and a sub-topic, prefer linking from the topic to the sub-topic. When topics are associated but not clearly identifiable as topic as sub-topic, choose an arbitrary link, link bidirectionally, or link from a common parent topic. Treat niches similarly.

### context folders

Project, area, and gig contexts may be converted to a folder, rather than being represented by a single note. In this case, the title of the note becomes the title of the folder and the note itself is renamed `INDEX.md` and moved into the context folder. This provides a means of working across multiple files within a clearly delimited boundary. Files outside of this folder may link to the context (represented by `INDEX.md`), but not to specific files within it.

### note identifiers

Every note has an ID `<note-id>`, stored under the key `id:` in the YAML frontmatter.

By default, `<note-id>` for a digital note (_"e-note"_) is `e` followed by a base-36 representation of the date in seconds since June 15, 1990 00:00 UTC, incremented as needed upon creation to avoid collisions.

If such a note is converted into a _paper zettel_, then it will additionally be assigned a _folgezettel_, recorded in the field `fz:` in the YAML frontmatter. The folgezettel starts with the letter `n` (_"narrative note"_) unless it is a _"technical note"_, in which case it starts with the letter `t`. The folgezettel string follows the initial letter (`n` or `t`) with a number and continues to alternate letters and numbers. A child note is created by using the parent's folgezettel as a prefix and then appending either:

- a number if the parent's folgezettel ends with a letter; or,
- a letter if the parent's folgezettel ends with a number

Sibling notes have the same parent and only differ in the last number/letter.

For notes in `bib/`, the field `id:` is the letter `b` followed by Zotero's internal key for the corresponding item, converted to lower case. The note also includes `citekey:` in the frontmatter which gives the citation key generated by Better Bibtex.

The filenames of notes use the following cases:

| Location   | `fz:` set? | Filename pattern                | Example                                       |
| ---------- | ---------- | ------------------------------- | --------------------------------------------- |
| Not `bib/` | No         | `<note-title> (<note-id>).md`   | `Gardening project (ebbpni).md`               |
| Not `bib/` | Yes        | `<note-title> (<note-fz>).md`   | `A zettel note is atomic (n2b1).md`           |
| `bib/`     |            | `<citation-key> (<note-id>).md` | `turingComputingMachinery1950 (bd3nabp6d).md` |

If a link to a note is broken after updating its filename based changing the note title, the citation key, or assigning a `fz:` value, then it can be recovered from `id:`.

### entrypoints

#### Home index

`Home.md` includes links to the zettel index, the topic indexes, the bib indexes, the niche indexes, the area index, and the project indexes.

It also lists working projects (those under `Notes/project/w`), organized by _context track_:

- _Research_

  Only three research projects may be active, one for each of the sub-categories:
  - _Primary_ for the research project which is the primary focus of my attention
  - _Secondary_ for the research project which I am beginning work on
  - _Explore_ for a research project or area I am beginning to explore

- _Academia_
- _Make_
- _Infrastructure_
- _Personal_

#### zettel index

A markdown file is used as an index for the zettelkasten. Every zettel should either be in the index or linked to by another zettel.

#### project index

An index of queued projects is maintained at `Notes/project/q/INDEX.md`, in an order roughly corresponding to their priority, and categorized under headings representing different tracks, including: _Research_, _Academia_, _Make_, _Infrastructure_.

Every top-level queued project should always appear in the project index, even if it belongs to an area.

An analogous project index is maintained for maybe projects, at `Notes/project/m/INDEX.md`.

Every top-level area is also represented in a list of areas.

#### topic and niche indexes

Indexes for topics and niches with status _queued_ or _maybe_ are analogous to those for projects.

#### area index

The area index, maintained at `Notes/area/w/INDEX.md`, provides a link to every area in `Notes/area/w`.

#### bib index

Similarly, queued bib items are listed in a bib index at `bib/q/INDEX.md`. The bib items are organized under the following bibliographic tracks in order of priority:

- _Research_
  - _Papers_
  - _Talks_
  - _Textbooks_
  - _Courses_
  - _Topics_
- _Articles_
- _Books_
- _Shorts_ (Youtube, etc.)
- _Movies_
- _Software_

An analogous index also maintained for maybe bib items, organized by the same tracks.

### frontmatter as launcher

A note's YAML frontmatter provides a field listing URLs (`urls:`) and a field listing local repositories (`repos:`). Functions and keymaps are defined for opening all URLs and repositories associated with the note. For project, gig and area contexts, this means that the note becomes the primary entrypoint for working within that context.

### notebook keymaps

The proposed notebook keymaps may be adapted to various editors.

Each notebook keymap starts with a prefix to determine whether a note is being created, searched, etc. The keys which follow correspond to the operational status, note status, target status and note type (in that order).

For example, in Neovim, I use the prefix `<space>j` to search all notes. Following this keymap with the keys `oqp` will search _operational_, _queued_ projects. Similarly, `<space>n` followed by `oqp` is used to create a new note for an operational, queued project.

Keys in the sequence may be omitted, in which case they will match the configured default. For example, following the prefix `<space>j` with only `p` will match all projects with the default range of matches for operational status and target status.

The key `<space>` may be used to terminate the sequence with all remaining elements being matched against the pre-configured default.

For all note types and target statuses, the corresponding keypress is the first letter of its name (e.g. `p` for `project/`, `b` for `bib/`). Indeed the names of these have been selected to avoid conflicting first letters. The only exception is for `anki`, which is represented by `k`. The top-level folders `Inbox/`, `Drafts/`, `Maybe/` and `Vault/` are represented with their first letter capitalized instead.

The keymap which reassigns statuses and note types takes only a single target as input, instead of a sequence. For example, in Neovim, the prefix `<space>m` is used to move notes, and then followed by a single key to indicate the target status or note type being assigned, such as `q` for `queue` or `V` for `Vault`.

## paper notes

A physical collection of notes is used alongside the digital notebook. Each note in this collection is a card.

The paper note collection has both an _inbox_ for intake and a _maybe_ section. Both are ordered by last time of access.

The zettel notes in this collection map directly to digital copies. The assumed workflow is rough hand-written copies of a paper note in the physical position it will occupy in the paper zettelkasten. The note eventually gets typed and added to the digital notebook, and then printed and added back to the physical zettelkasten. If the note requires hand-drawn figures, it may remain as hand-written. Different coloured cards are used to distinguish rough cards from those which have been finalized.

Additional paper sections are available, intended to complement corresponding elements of the notebook rather than duplicate them. There is a section for bib items and a section for experiences.

There is also a section which combines contexts (project, gig, area) and collections (topic, niche). Each context or collection may constitute multiple cards. They are separated by tabbed separators.

All sections except for zettels are organized by last time of access, and brought to the front of the filing system after having been accessed (Noguchi method). Some of the paper content may eventually be added back to the digital notebook, but this is not necessary.

## bibliography

The bibliography is managed with Zotero. A script creates a corresponding markdown file for each Zotero item. This file imports some of the associated bibliographic metadata from Zotero in the YAML header of the markdown file. The body of the markdown file is used for notes related to the bibliographic item and to link to other notes which make reference to it.

By default, imported bib items are given target status `i`. After import, they should be moved to another appropriate target status. The import script should not create duplicate notes for the same Zotero item, but metadata should be updated regardless of which target status the item has been assigned.

Citations within notes are represented by links to the markdown file corresponding to the bibliographic item. Since these files have names based on the Zotero citation key, string replacement can be used to convert these to references supported by other tools like Pandoc and other formats like Latex.

## tasks

Tasks may be associated with a project, gig or area context, or they may stand alone.

Tasks may have the following task statuses:

- `+inbox`
- `+next`
- `+maybe`
- `+followup`
- `+done`

A task may be assigned a `scheduled` date and/or a `due` date.

An _Inbox Report_ should show all tasks with status `+inbox` and should be processed alongside notes in `Inbox/`.

A _Maybe Report_ should show all tasks with status `+maybe`.

The _Next Report_ should show tasks which:

- do not have an associated context and are not tagged `+inbox`, `+maybe`, `+followup`, `+done`
- (have an associated context, or are tagged `+followup`) and have at least one of the following:
  - a `scheduled` value in the current week or earlier
  - a `due` value next week or earlier

Otherwise, work should occur within a particular context or task track.

A _Context Report_ should be available for each project, gig or experience context, listing all the tasks associated with that context. A task should be identified with the note ID of the associated context to handle cases where the context title drifts. For example, in Taskwarrior, I assign the value `<note-slug>-<note-id>` to the `project:` field so that `<note-id>` can be used as a persistent source of truth.

In this way, tasks are partitioned between the Next Report and specific Context Reports. Only tasks with `scheduled` and/or `due` values can appear in both a Context Report and the Next Report.

The reason for concealing items associated with a context is because the completion of tasks associated with a context is typically performed by time-blocking for that context. Tasks which do not have a `scheduled:` or `due:` value will be performed when working within a time block allocated to that context.

Additionally, items may be associated with a _task track_ when there are particular circumstances where performing that task would be suitable. I use the following task tracks:

- `@admin` for administrative work
- `@buy` for things to be purchased online
- `@email` for email and text-based communications
- `@home` for tasks to be completed at home (usually chores)
- `@phone` for phone calls
- `@quest` for errands

Each task track should have an associated report, enabling a view of tasks suitable for particular circumstances.

## intake process

### inbox note intake

`Inbox/` is used to capture notes from various sources. The `Inbox/` should be emptied once per day by applying one of the following decisions to each note it contains:

1. Delete or archive the note if it is no longer relevant.
2. If the note is a task, move it to the task system and delete the note.
3. If the note is a calendar event, add it to a calendar and delete the note.
4. If the note is a referent note, move it to the folder corresponding to its note type and assign a target status. If the target status is `q` or `m`, add it to an appropriate track in the corresponding list.
5. Otherwise, if the note will be developed into a non-referent note, move it to `Drafts/` if it is intended for completion or to `Maybe/` if it is uncertain whether it will be completed.

### inbox task intake

Along with `Inbox/`, the task inbox should also be emptied once per day. For each task tagged `+inbox`, apply the first of the following decisions which applies (and remove the tag `+inbox`):

1. Delete the task if it is no longer relevant.
2. If it can be done in 2 minutes, do it immediately.
3. If the task depends on someone else, tag it `+followup`.
4. If the task is associated with a context, tag it with that context. If the context is a project, it should have at least one item tagged `+next`. Apply the `+next` tag to the current item if appropriate.
5. If the task is not associated with a context, simply tag it `+next`.

When applying either #3, #4 or #5, a task may also be tagged with a `scheduled` date, a `due` date, and/or a task track.

### bib intake

The Zotero import script should be applied multiple times per week. After import, each new item in `bib/i/` should be assigned a target status. If tagged `q` or `m`, the item should be added to an appropriate track in the corresponding list.

### drafts/maybe intake

The `Drafts/` folder is a folder revisited frequently for content to be finalized. The note type of draft items is emergent and a single draft note may eventually be partitioned into multiple notes.

The `Maybe/` folder is reviewed occasionally when time allows and when inspiration is lacking.

Notes in `Drafts/` or `Maybe/` have typically arrived there because they are non-referent. However, if they are deemed referent, then they are moved into `Notes/` immediately.

Otherwise, a note moves into one of `zettel/`, `forma/`, `yarn/` or `unknown/` when the note reaches maturity. It may still be edited later on.

If a note in `Drafts/` or `Maybe/` reaches a state where further edits are not planned, but I wish to include it in `Notes/`, then it should be moved to `yarn/`, which allows for arbitrary internal structuring of notes.

## software

This workflow can be implemented with:

- `neovim`
- `zk` and the associated Neovim plugin `zk-nvim`.
- `taskwarrior`, where the `projects:` field is used specify project, area, and gig contexts
- `vit`

Alternatively, the workflow may be adapted to Obsidian or various other applications.

## references

The Zettelkasten approach of organizing hyperlinked zettels in a non-hierarchical manner was the core source of inspiration for this notebook's organization. My understanding of the Zettelkasten method was informed most of all by the following resources:

- [How to Take Smart Notes](https://www.goodreads.com/en/book/show/34507927-how-to-take-smart-notes) by Sönke Ahrens
- [A System for Writing](https://www.goodreads.com/book/show/214971755-a-system-for-writing) by Bob Doto
- [zettelkasten.de](https://zettelkasten.de/)

The task management approach follows [Getting Things Done](https://en.wikipedia.org/wiki/Getting_Things_Done) by David Allen, with the following mods:

- Project, gig and area contexts are treated separately from the Next Report. Working on tasks within clearly scoped contexts is preferred, rather than working from a single task list.
- Limits on the number of projects in progress are imposed, and a project queue is maintained.

Organization based on projects and areas of responsibility comes from Tiago Forte's [PARA method](https://fortelabs.com/blog/para/), with the following mods:

- While PARA emphasizes organizing within clearly scoped project and area contexts, this notebook aims to enable working out of context as well. This motivates the incorporation of a zettelkasten, topics, and other note types rather than the single `Resources` section recommended by PARA.
- Instead of having a single broad `Resources` section, content which does not belong to projects or areas is assigned to various other types, with an emphasis on separating knowledge work from information which is used for personal organization.
- The category _gigs_ is used separately from _projects_ for contexts such as travel and events which work towards a goal without producing a deliverable.
