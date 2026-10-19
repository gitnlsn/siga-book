# Siga

Manuscrito em Markdown; EPUB pronto para a KDP e PDF pronto para impressão do
outro lado. Mesma cadeia de ferramentas de *Quarenta dias úteis*, *Manual da
Vida* e *What Remains*.

    make deps                  # uma vez, no macOS
    make                       # constrói o livro
    make check                 # preflight contra o que a KDP recusa
    make marcadores            # o que ainda está em aberto
    make release               # constrói e confere tudo
    make new-book SLUG=<slug> TITLE="..."   # o próximo livro

Romance avulso: *Siga* (`BOOK=siga`), com a edição em inglês *Sixty-One
Percent* (`BOOK=sixty-one-percent`). `make traducao` lista os capítulos em
inglês atrás do original.

## Layout

    books/<slug>/
      book.yaml              metadados, formato, número na série, anúncio na KDP
      front/                 o que vier antes             (fólios romanos)
      chapters/              o romance                    (fólios arábicos)
      parts/                 aberturas das 4 partes
      back/                  o que vier depois
      illustrations/masters/ originais em alta, um por parte
    docs/
      kdp-upload.md          o passo a passo do upload
      <slug>/
        outline.md           premissa, os 4 arcos, fonte única dos capítulos
        bible.md             o mundo daquele livro
        timeline.md          a cronologia
        references.md        o que é real, e onde foi conferido
        translation-en.md    títulos, glossário e frases fixas em inglês
      _modelo/               os arquivos em branco, para um livro novo
    shared/                  template de impressão, capa, CSS do EPUB, fontes
    scripts/                 build, gates, digest, stats, scaffolders
