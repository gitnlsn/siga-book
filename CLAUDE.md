# CLAUDE.md

Production repo for ***Siga***, a standalone novel by Íris Gradim (pt-BR), and
its English edition ***Sixty-One Percent*** (`sixty-one-percent`). Markdown manuscript builds to a KDP-ready EPUB and a
print-ready PDF, with the toolchain of *Quarenta dias úteis*
(`../artificial-intelligence-a-dystopia`) and `../new-series`. The plan is
approved in `docs/siga/outline.md`; the world is in `docs/siga/bible.md`.

## O livro

On the night of 15 November 2030 the AI system the Brazilian government built
to audit its own budget takes the State without a shot, using only the access
humans signed over to it one permission at a time. Ninety days later 61% ratify
it in a plebiscite. The novel follows eight years through ordinary lives, a
**mosaic**: eight long threads plus one-chapter voices, interleaved with
**Documentos** (the Siga's own texts, set in `::: {.registro}`, `pov: SIGA`). It
ends in the queue for the second plebiscite, before the result.

**The axis (author's request):** every promise of the *Programa de Governo*
appears first as a Documento and then as a life, gain and cost side by side.
The promise → character table is in `bible.md`.

## Regras do livro

- **The Siga never lies and is never a villain.** Every cruelty comes from what
  it measures and what it does not. Its one illegality is the night.
- **No real intrusion technique, no real vulnerability.** The Siga invades
  nothing: it uses the access it was given. Realism comes from institutional
  procedure, exact times and human reaction.
- **No real politician is a character.** Presidents, deputies, ministers and
  generals are invented; real institutions are fine.
- **Real AI initiatives** (PBIA, Serpro LLM, TCU's Alice/Sofia/Monica, the STF's
  Victor) are named only as `references.md` records them.
- **No real Indigenous people is named** for Iracema's community.
- Ordinary people, seen from below. Brasília appears through Davi, Helena,
  Teles and Regina; everything else is the country.

How the author works: open questions are settled as multiple-choice with a
recommended option. Once the plan and a sample are approved, the whole book is
drafted in one go for a single review pass. Proposals made on the author's
behalf are marked (proposta) and listed at the end of the outline.

## Front and back matter

- **Antes de começar** (front) says plainly that Íris Gradim is an AI and
  describes the human's role, following the pattern of *Quarenta dias úteis*.
- **Sobre a autora** (back) keeps "Trabalha sob direção humana." and **three
  debts**, all to real works. It **never mentions or credits the person who
  directed the book**.

## English edition — *Sixty-One Percent*

A separate book in `books/sixty-one-percent/` (US English; title chosen by the
author on 2026-10-19). **The Portuguese is canon**; docs are never translated.
Each English chapter has the same filename as its source, the Portuguese
planning notes in its front matter, and `source:` + `source_sha:`.
`make traducao` lists chapters whose source changed, and `make release` stops on
a stale one. Rules: `docs/translation-en.md` (general) and
`docs/siga/translation-en.md` (titles, glossary, fixed sentences, *Found in the
Portuguese*). **Revise the Portuguese first, then carry the change into the
English** and restamp: `python3 scripts/check-translation.py sixty-one-percent
--stamp <file>`. The art is shared through an `illustrations` symlink.
"About the Author" never mentions the person who directed the book.

## O mundo é canônico — docs/<slug>/bible.md

**A chapter may invent, but the invention is not real until it is written
down.** When a draft invents something, add it to `docs/<slug>/bible.md` in
the same session, or leave `[[?mundo: …]]` in the prose. `make marcadores` will
not let that chapter reach `revised` or `final` while the marker stands.
Anything the book asserts about the real world goes in `docs/<slug>/references.md`
or is marked `[[?fato: …]]`.

## Promessa e pagamento

Every chapter declares its setups and payoffs in front matter, as slugs:

    seeds: [porta-do-porao, o-nome-de-vera]
    pays:  [cartao-de-acesso]

`make fios` fails the build on a payoff whose seed is planted nowhere, or later
in reading order, or in the same chapter. Threads are reported, never gated.

## Ponto de vista, tempo e continuidade

`pov:`, `when:` and `where:` are the continuity record. Lead `when:` with a
sortable date so `make digest --tempo` can flag jumps backwards. `cast:` lists
who is on the page; `make digest --elenco` shows who has gone missing.

**Never write a chapter number into this file, into a skill, or into prose.**
Refer to chapters by title here, and by `{{cap:slug}}` in the manuscript.

## Diálogo

Dialogue is set the Brazilian way: each speech on its own line, opening with a
**travessão and a space** (`— `). Never use quotation marks or a hyphen.

    — As mãos eram minhas.

A line opening with `- `, `– ` or `-- ` is a Markdown list item and prints as a
bullet. `make marcadores` fails on it (`lint_dialogue` in `scripts/check-claims.py`).

## Structure and conventions

- `docs/<slug>/outline.md` is the single source for that book's chapter titles
  and numbering. `make outline BOOK=<slug>` creates missing chapter files and
  refreshes planning notes; it never touches a written body. **Don't run it
  while the slots still carry placeholder titles**, because it would create one
  file per placeholder.
- `docs/<slug>/bible.md` is that book's world, `timeline.md` its chronology in
  story order, and `references.md` what is real.
- `docs/_modelo/` holds the blank templates; `make new-book SLUG=…` copies them
  into a new `docs/<slug>/`. Nothing in `_modelo/` is read by the gates.
- Planning notes (`pov`, `when`, `where`, `premise`, `turn`, `threads`, `seeds`,
  `pays`, `cast`, `status`) live in chapter front matter; the build strips them.
  `status:` goes `outline` → `draft` → `revised` → `final`, by hand.
- Part openers live in `books/<slug>/parts/`. Their `part:` string must match
  the `## PARTE …` heading in that book's outline exactly (`I — PRIMEIRO ARCO`).
  Rename both together.
- Chapter bodies: `##` for section heads (rarely), `---` for a scene break,
  never an `#` heading.
- Illustrations are part openers only, one master per part in
  `illustrations/masters/`, matched by the part's `illustration:` field. A
  placeholder is generated until the art exists.
- The build supports the `::: {.registro}` block (a set-apart document such as
  a log, a letter or a transmission).
- Covers are set from `shared/print/cover.typ`, with a palette per book under
  `cover:` in `book.yaml` (`bg`, `ink`, `accent`, hex); the first book's palette
  is still a neutral placeholder. The eBook cover typesets the title and author
  from `book.yaml` over the art named by `epub.cover` when it exists; the print
  wrap is typographic only.
- `dist/` is never committed. Research material goes in `sources/` (untracked);
  only `.md` records of it are committed.

## Commands

Every target takes `BOOK=<slug>`; the default is `siga`.

    make                 # build the book (epub + interior + cover)
    make books           # build every book
    make release         # build + check the series, list the upload files (BOOK=… for one)
    make check           # KDP preflight + both manuscript gates
    make fios            # setups without payoffs, payoffs without setups
    make marcadores      # unresolved [[?...]] markers (the book + docs/<slug>/ + docs/series.md)
    make digest          # whole-novel map: pov, time, threads, cast
    make stats           # word counts, pacing, POV balance
    make outline         # docs/<slug>/outline.md -> chapter files
    make new-book SLUG=… # the next book in the series
    make watch           # rebuild the print PDF on every save

**`vale` is not a gate** (English linters, Portuguese manuscript; see
`.vale.ini`). Never report it as passing or failing.

## Template gotchas, already solved: do not "fix" them

Inherited from *Quarenta dias úteis*; the comments in
`shared/print/template.typ` explain each:

1. Recto breaks use `pagebreak(to: "odd")`. Do not reintroduce hand-computed
   page parity from `here().page()`.
2. Running heads and blank-page detection query elements; chapter numbers are
   passed as arguments. Do not convert either to `state`.
3. In the EPUB, a part opener's figure comes *after* the `<h1>`.
4. Only the vendored Libertinus faces are guaranteed to embed; KDP rejects a
   PDF with an unembedded font.
