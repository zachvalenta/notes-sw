# ⛩️

## 参考

🗄️
* `data/modeling.md`
* `plt.md` LSP

## 进步

* _24_: split into own file, config fmts (Cuelang, INI, KDL, YAML)
* _21_: start thinking about encoding as a thing

# 🗃️ CONFIG

📙 Kleppmann ch. 4
🗄 `src` secrets

* aka data languages 📙 Thomas pragmatic programmer [60]

---

generate from CLI usage https://github.com/nickgerace/gfold

JSON5 https://json5.org/
https://drewdevault.com/2021/07/28/The-next-YAML.html

QUERY TOOLS
* query Google Sheets with SQL https://github.com/julien040/anyquery
* _qq_: https://github.com/JFryy/qq
* https://github.com/simonw/sqlite-utils
* https://github.com/datafold/data-diff
* https://github.com/dinedal/textql
* https://github.com/noborus/trdsql

## Cuelang

📜 https://cuelang.org/

SYNTAX 🎗️ can convert to JSON and YAML
```json
// Define a schema for a person
person: {
    name: string & len(name) > 1 // Name must be a string and at least 2 characters long
    age:  int & >= 0             // Age must be an integer and at least 0
    email: string & =~ "^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\\.[a-zA-Z]{2,}$" // Valid email format
}

// Instance of a valid person
person: {
    name:  "John Doe"
    age:   30
    email: "johndoe@example.com"
}
```
```sh
# validate
cue vet person.cue
```

---

* parser https://github.com/benhoyt/inih
* use cases https://news.ycombinator.com/item?id=34074386 https://chatgpt.com/c/670d7768-62c8-8004-89e2-fd5a876700d7
* alternative https://github.com/bazelbuild/starlark https://github.com/systeminit/si
* not supported by VS Code's Markdown syntax highlighting https://stackoverflow.com/a/70456058/6813490 https://highlightjs.readthedocs.io/en/latest/language-requests.html

## INI

* used by `.gitconfig`
* comments: `;`, hash (for Git at least)
* _pyinilint_: validate https://pypi.org/project/pyinilint/ https://gitlab.com/danieljrmay/pyinilint alternative https://github.com/Boeing/config-file-validator

## KDL

https://kdl.dev/ https://zellij.dev/documentation/layouts
> this is what started me to split protocols into own file apart from `computation.md`

## TOML

* link https://github.com/tamasfe/taplo 🗄️ yazi config
> VS Code plugin 'Even Better TOML'

* https://github.com/hukkin/tomli-w
```python
import tomllib
import tomli_w

# READ
def load_config():
    config_path = Path(__file__).parent.parent / '.env'
    logger.info(f'config path: {config_path}')
    with open(config_path, 'rb') as f:
        return tomllib.load(f)
config = load_config()
logger.info(f'SFTP conf: {config['sftp']}')

# WRITE
def update_config(key, val):
    fpath = Path(__file__).parent / '.env'
    with open(fpath, 'rb') as f:
        config = tomllib.load(f)
    config[key] = val
    with open(fpath, 'wb') as f:
        f.write(tomli_w.dumps(config).encode())
    logger.info(f'{key} ➡️ {val}')
```
```toml
[sftp]
protocol="sftp"
host="sftp.spscommerce.com"
port=10022
user="cappinc"

[filepaths]
new-item = "testin/capp-new-items-{date}.edi"
pricing = "testin/capp-pricing-{date}.edi"
lead-time = "testin/capp-lead-time-{date}.edi"
```

## XML

🗄️ `algos.md` tree

* usage: EDI, Maven, Claude https://github.com/simonw/files-to-prompt
* element types: prolog, root node/element, child node/elements, comments (same as HTML)
* query https://github.com/gawel/pyquery
* _XSLT_: CSS for XML https://github.com/azoner/pyx12
* _XPath_: CSS selector for XML

---

HISTORY
* _cXML_: owned by SAP https://en.wikipedia.org/wiki/CXML https://cxml.org/
* https://news.ycombinator.com/item?id=35467711
* previously more popular 📙 Beaulieu 2.34

## YAML

YQ 📜 https://github.com/mikefarah/yq
* edit
* query
* to JSON
* Github Action
```sh
yq 'true' $FILE  # validate https://mikefarah.gitbook.io/yq/upgrading-from-v3#validate-documents
```

SYNTAX 📜 https://yaml.org/
* spacing/indentation err: `mapping values are not allowed in this context` https://chatgpt.com/c/671d7065-3644-8004-9967-e49a83ef4810
* scalars
```yaml
name: John Doe                # string
age: 30                       # int
height: 1.75                  # floating-point
is_employee: true             # boolean
nickname: null                # null
```
* list/map
```yaml
# SEQUENCE/LIST
languages:
  - Python
  - JavaScript
  - Go

# MAP/DICTIONARY
address:
  street: 123 Main St
  city: Sampleville
  zip_code: 12345

# NESTED
projects:
  - name: Project Alpha
    team:
    completed: false
      - name: Alice
        role: dev
      - name: Bob
        role: design
  - name: Project Beta
    completed: true
    team:
      - name: Carol
        role: pm
      - name: Dave
        role: dev
```
* anchors
```yaml
default_user: &default_user
  name: John Doe
  email: johndoe@example.com
  roles:
    - user
    - editor

users:
  - <<: *default_user  # use anchor
    id: 1001
  - <<: *default_user  # use anchor + override
    id: 1002
    name: Alice Doe
    email: alicedoe@example.com
```

# 📜 DOCUMENTS

## Canva

```txt
Design simplicity over PDF functionality:
* WYSIWYG interface
* Templates
* No learning curve
* Cross-platform web access

Image-based output advantages:
* Exact visual reproduction across devices
* No font/layout issues
* Harder to copy/modify content
* Smaller file size than vector for complex designs

Key tradeoff: Sacrifices PDF features for:
* Accessibility (screen readers can't read text)
* Search functionality
* Text selection/copying
* Easy modification
* Bookmarks/ToC/links

Canva's target market (marketers, small business owners, non-designers) typically prioritizes visual consistency and ease of creation over PDF functionality. They often don't even know what they're giving up.
```

get sections with `pdftk`
```sh
pdftk "contemporary piano.pdf" update_info bookmarks.txt output output.pdf
```
```txt
BookmarkBegin
BookmarkTitle: TOC
BookmarkLevel: 1
BookmarkPageNumber: 7
BookmarkBegin
BookmarkTitle: ch 1 - basics
BookmarkLevel: 1
BookmarkPageNumber: 9
```

## LaTeX

🗄️ `design.md` typography
📙 https://www.manning.com/books/how-computers-make-books

* https://github.com/googlefonts/fontations
* _fnt_: manager https://github.com/alexmyczko/fnt
* Pollen https://docs.racket-lang.org/pollen/ https://news.ycombinator.com/item?id=20029372
* TeX https://news.ycombinator.com/item?id=20027807 https://news.ycombinator.com/item?id=7823337 https://news.ycombinator.com/item?id=7822057 https://news.ycombinator.com/item?id=20027116
* BYO https://news.ycombinator.com/item?id=38421452

LaTeX code consists of commands and environments to format text or mathematical expressions.
```latex
\documentclass{article}
\begin{document}
Hello, this is a simple LaTeX document.

Here is a math equation:
\[
E = mc^2
\]

This is inline math: $a^2 + b^2 = c^2$.
\end{document}
```

To render LaTeX code, you need a LaTeX editor or engine. Here are some options:
* MacTeX (macOS)
* VS Code with LaTeX extensions
* Overleaf, Markdown https://brainbaking.com/post/2021/02/writing-academic-papers-in-markdown/
* If you’re using a Jupyter Notebook, you can render LaTeX with Markdown cells:
* Use libraries like matplotlib, sympy, or IPython for LaTeX rendering.
* Save the code as `example.tex`. Compile using a LaTeX engine -> Command line: pdflatex example.tex

LaTeX is commonly used to create:
* Research papers
* Resumes
* Presentations (with Beamer)
* Books

Useful Packages:
* amsmath: Advanced math formatting
* graphicx: For including images
* hyperref: For hyperlinks
* geometry: For page layout adjustments

* http://www.danielallington.net/2016/09/the-latex-fetish/
* https://increment.com/open-source/the-lingua-franca-of-latex/
* alternative https://sile-typesetter.org/
* https://news.ycombinator.com/item?id=35242299
* https://news.ycombinator.com/item?id=35250210
* Typst https://www.youtube.com/watch?v=sWmlbMh3ol8

## Markdown

🔗 https://www.markdownguide.org/
🛠️ jq for Markdown https://github.com/yshavit/mdq

SPEC
* footnotes https://github.blog/changelog/2021-09-30-footnotes-now-supported-in-markdown-fields/
```md
Here is a simple footnote[^1].

[^1]: My reference.
```

FLAVORS https://news.ycombinator.com/item?id=43137616
* _Djot_: https://djot.net/ https://www.jonashietala.se/blog/2024/07/09/microfeatures_in_my_blog/
* _CommonMark_: https://meta.stackexchange.com/q/348746
* _GFM_: https://github.com/github/markup/issues/498#issuecomment-158257453 
* _MyST_: https://github.com/executablebooks/MyST-Parser

PARSERS
* _micromark_: https://github.com/micromark/micromark
* _MDX_: jsx in markdown (for tables, charting) by transpiling Markdown to JS via JS runtime (e.g. React) and then running in the browser https://github.com/mdx-js/mdx/ https://signalsandthreads.com/writing-technically/ re: Next https://zackproser.com/blog/maintaining-this-site-no-longer-fucking-sucks
* time suck https://www.joshwcomeau.com/blog/how-i-built-my-blog-v2/
* _markdown-it-py_: used by rich https://github.com/executablebooks/markdown-it-py https://pythonbytes.fm/episodes/show/320/the-bug-is-in-the-javascript
* _commonmark_: https://github.com/readthedocs/commonmark.py https://github.com/Textualize/rich/pull/2439/files
* _goldmark_: https://github.com/yuin/goldmark
* HTML to Markdown https://github.com/JohannesKaufmann/html-to-markdown https://html-to-markdown.com/

RENDER
* _frogmouth_: https://github.com/Textualize/frogmouth
* _glow_: ✅ https://github.com/charmbracelet/glow
* _mdcat_: ✅ https://github.com/swsnr/mdcat https://github.com/charmbracelet/mods/blob/main/examples.md
* _rich_: https://rich.readthedocs.io/en/latest/markdown.html

EDITOR
* https://simplemde.com/ https://tunalog.org/en-us/index.html

---

* _markdown_: https://pypi.org/project/markdown2/ used this one for `m2h` https://github.com/Python-Markdown/markdown had issues with ampersands in URLs, see repo commit `43e` https://stackoverflow.com/a/20593644/6813490 https://stackoverflow.com/questions/39086/search-and-replace-a-line-in-a-file-in-python
* https://codehike.org/blog/the-curse-of-markdown
* writing on mobile, comments for editing https://conroy.org/blogging-on-paper
* vs. RST https://buttondown.com/hillelwayne/archive/why-i-prefer-rst-to-markdown/
* use image (w/ Github renderer) https://github.com/catppuccin/python/blob/main/README.md

* links https://jordanelver.co.uk/blog/2021/03/13/til-about-markdown-reference-style-links/
* convert to HTML with Vim http://vimcasts.org/episodes/converting-markdown-to-structured-html-with-a-macro/
* Github https://docs.github.com/en/issues/tracking-your-work-with-issues/about-slash-commands
* RENDERME https://news.ycombinator.com/item?id=30336703
* metadata https://github.com/blacksmithgu/obsidian-dataview
* spec https://github.blog/2017-03-14-a-formal-spec-for-github-markdown/
* asciidoc vs. Markdown https://news.ycombinator.com/item?id=27744509
* href https://github.com/pemistahl/grex
* linting https://mkaz.blog/code/linting-markdown-syntax/
* formal spec https://githubengineering.com/a-formal-spec-for-github-markdown/
* code syntax support https://github.com/github/linguist/blob/master/lib/linguist/languages.yml
* Pandoc has their own version of Markdown? https://yihui.name/en/2018/09/target-blank/
* Markdown to PowerPoint https://yhatt.github.io/marp https://www.youtube.com/watch?v=CkIweDviGH8
* HTML to Markdown https://github.com/JohannesKaufmann/html-to-markdown
* [dropdowns!](https://raw.githubusercontent.com/30-seconds/30-seconds-of-code/master/README.md)
* [diff](https://stackoverflow.com/a/40883538)
* table fmt: Jira, Markdown/RST, Latex https://jsvine.github.io/intro-to-visidata/basics/saving-sheets/
* Markdown for Google Docs https://www.theverge.com/2022/3/29/23002138/google-docs-markdown-support-formatting-update
* Docbook as predecessor 📙 Thomas pragmatic programmer [254]

conversion to HTML
* https://github.com/susam/texme
* Markdown to HTML w/ Python CLI https://python-markdown.github.io/cli/ `python -m markdown 1997-graham-hackers-painters.md > pg.html` -> doesn't handle quotes, output is vanilla would need to figure way to add CSS
* _mistune_: https://github.com/lepture/mistune
* _markdown_: `python -m markdown rn.md > rn.html` https://python-markdown.github.io/cli/ used in MkDocs https://github.com/mkdocs/mkdocs/blob/master/requirements/project.txt
* _markdown2_: https://github.com/trentm/python-markdown2 supports (maybe) ghfm https://github.com/mkdocs/mkdocs/issues/263#issuecomment-65362418
```sh
python -m markdown2 --extras fenced-code-blocks my-debug-checklist.md > debug.html
```

add styles
* `water.css` w/ Beatiful Soup in script https://stackoverflow.com/a/19123463/6813490 
* more advanced https://github.com/cburmeister/cburmeister.github.io/blob/master/Makefile pandoc https://serverless.pub/lambda-utility-layers/ https://github.com/kickstartcoding/cheatsheets

## PDF

GENERATE
* _invoice_: https://github.com/maaslalani/invoice https://github.com/charmbracelet/pop

READERS
* _baca_: ebook/epub TUI reader https://github.com/wustho/baca
* _tdf_: https://github.com/itsjunetime/tdf
* _termpdf_: kitty https://github.com/dsanson/termpdf.py

TO TEXT
> why this is still hard https://arstechnica.com/ai/2025/03/why-extracting-data-from-pdfs-is-still-a-nightmare-for-data-experts/
* _markitdown_: 🎯 AI = 25k stars in a month https://github.com/microsoft/markitdown
* _parsr_: https://github.com/axa-group/Parsr
* _poppler_: https://poppler.freedesktop.org/
```sh
$ brew info poppler
Conflicts with:
  pdf2image (because poppler, pdftohtml, pdf2image, and xpdf install conflicting executables)
  pdftohtml (because poppler, pdftohtml, pdf2image, and xpdf install conflicting executables)
  xpdf (because poppler, pdftohtml, pdf2image, and xpdf install conflicting executables)
```
* everything else seems to rely on it https://github.com/sxyazi/yazi https://github.com/search?q=repo%3Amodesty%2Fpdf2json%20poppler&type=code https://github.com/search?q=repo%3Ajalan%2Fpdftotext%20poppler&type=code https://github.com/jalan/pdftotext

---

* https://registerspill.thorstenball.com/p/joy-and-curiosity-37
* internals https://github.com/desgeeko/pdfsyntax/blob/main/docs/browse.md https://news.ycombinator.com/item?id=43000303
* https://realpython.com/pdf-python/
* https://github.com/Halolegend94/pdf4py
* Sioyek https://news.ycombinator.com/item?id=34069804
* https://docs.racket-lang.org/quad/
* Markdown https://docs.racket-lang.org/quad/
* https://rtpg.co/2016/09/17/make-an-ebook.html
* _design_: https://news.ycombinator.com/item?id=24108950 https://gds.blog.gov.uk/2018/07/16/why-gov-uk-content-should-be-published-in-html-and-not-pdf/
* _annotation_: PDF Expert, Flexcil, https://news.ycombinator.com/item?id=23230218 https://github.com/xournalpp/xournalpp
* _archival_: https://github.com/danburzo/percollate https://github.com/pirate/ArchiveBox
* _readers - macOS_: PDF Expert (freemium version won't let you save) PDF Element ($90/year) Preview (search doesn't seem to work for most documents https://duckduckgo.com/?q=macos+preview+search+doesn%27t+work&atb=v161-1&ia=web text in sidebar doesn't correspond to hightlight, some hightlights produce no text in sidebar, can't enter emoji into notes, limited keyboard shortcuts) Nitro PDF
* _to plain text_: https://github.com/axa-group/Parsr https://github.com/jsvine/pdfplumber
* _from plain text_: http://richardmavis.info/using-web-technologies-to-print-a-book https://coreyburmeister.com/continuous-integration-and-deployment-for-my-resume/
* _from HTML_: https://jvns.ca/blog/2020/06/19/a-little-bit-of-plain-javascript-can-do-a-lot/ https://www.princexml.com/
* _split_: select subset and drag into Finder
https://github.com/jorisschellekens/borb
https://news.ycombinator.com/item?id=26691626
* _ereader_ https://johnfactotum.github.io/foliate/
[PDF is bad]()
* PDF reader w/ Vim bindings: Zathura http://jhshi.me/2016/03/09/zathura-pdf-viewer-for-vim-lovers/index.html#.Xg4gThdKh-U not available on macOS https://www.reddit.com/r/vim/comments/3prfd0/pdf_reader_with_vim_keybindings_for_mac_osx/
* https://github.com/burtonator/polar-bookshelf https://pwmt.org/projects/zathura/ https://goodreader.com/
* mobile: [Joplin](https://github.com/laurent22/joplin), IAWriter
* https://www.pdfa.org/a-technical-and-cultural-assessment-of-the-mueller-report-pdf/

# 🪪 ENCODING

🔍 https://bestasciitable.com/
⏳ history https://www.youtube.com/watch?v=DlQvSs99UIw

---

OVERVIEW https://www.youtube.com/watch?v=DntKZ9xJ1sM
* _ASCII_: maps character to bit e.g. `A` -> 1000001 (65)
* _Unicode_: maps character to code point e.g. `A` -> U+0041
* _code point_: hex repr character
* _UTF-8_: maps Unicode code point to byte sequence https://csvbase.com/blog/9
* variable length = can use single byte for `A` but more bytes (up to 4) if necessary

https://en.wikipedia.org/wiki/Character_encoding

```sh
# app reads bytes from disk
1101000 1100101 1101100 1101100 1101111 
# app uses UTF-8 to decode
104 101 108 108 111 
# app uses Unicode
"hello"
```

CHARACTER SET
* _Unicode_: character set https://stackoverflow.com/a/13212528
* i.e. way to identify each character uniquely https://practicaltypography.com/ligatures-in-programming-fonts-hell-no.html
* _character set_: KV set in which K = characters and V = code point e.g. A = 41
* single byte (Latin) vs. multibyte (Japanese) 📙 Beaulieu [21]
* _code point_: numerical value in character set e.g. `0x0394 `https://www.fluentpython.com/lingo/#code_point 📍 https://www.textualize.io/blog/posts/7-things-about-terminals
* file types have https://the.exa.website/features/icons

encoding
* UTF-8: encoding
* encoding: algo that transforms number to binary and vice versa
```python
def utf8(num):
    return binary

utf8(1)  # 00000001
utf8(2)  # 00000010
utf8(3)  # 00000011
utf8(4)  # 00000100
```

* 📙 Bryant computer systems chapter 1
* _error correction_: 📙 MacCormick 5 https://en.wikipedia.org/wiki/Error_detection_and_correction
* _code point_: char https://en.wikipedia.org/wiki/Code_point https://www.joelonsoftware.com/2003/10/08/the-absolute-minimum-every-software-developer-absolutely-positively-must-know-about-unicode-and-character-sets-no-excuses/ 

* _iconv_: convert encoding https://kadekillary.work/post/cli-4-ds/
* emoji https://darrenburns.net/posts/unicode-emoji/

DIGRAPHS
* digraph: two letters forming single phoneme e.g. "ea" in "bread"
* __digraph__: Unicode char not on typical keyboard e.g. °∆ http://vimdoc.sourceforge.net/htmldoc/digraph.html#digraph-table
* specified in RFC 1345 https://datatracker.ietf.org/doc/html/rfc1345
* `^M` = DOS newline/carriage return; rm with `sed -i '' 's/\r//g'` (can also use vim, tr, dos2unix) 🗄️ `analytics.md` visidata

https://en.wikipedia.org/wiki/Mojibake
https://terminaltrove.com/lemmeknow/
https://github.com/abhimanyu003/sttr


* `\r`: carriage return https://stackoverflow.com/a/1761086/6813490
* `\n`: new line
* `\t`: in a string literal is an escape sequence for tab character, horizontal whitespace, ASCII codepoint 9 https://stackoverflow.com/a/22116523/6813490

* _EOF_: not a char https://ruslanspivak.com/eofnotchar/
* `%`: binary character indicating that there's no new line
* _BOM_: https://www.fluentpython.com/lingo/#BOM
* en-dash, m-dash, hyphen https://www.punctuationmatters.com/en-dash-em-dash-hyphen/

* `r`: carriage return https://stackoverflow.com/a/1761086/6813490
* `n`: new line
* `\t`: in a string literal is an escape sequence for tab character, horizontal whitespace, ASCII codepoint 9 https://stackoverflow.com/a/22116523/6813490

## semantics

* _encode_: 动 convert to diff fmt 📙 MacCormick 5.66
* typically byte per/char https://stackoverflow.com/a/31322359
> Each byte represents some text character in the program. 📙 Bryant 1.1
* multibyte = n byte per/char e.g. Japanese 📙 Beaulieu 2.19
* can be anything e.g. Morse code (dot/dash to text) 📙 Sweigart 1.3
* QR/bar code https://boonepeter.github.io/posts/2020-11-10-spotify-codes/ https://news.ycombinator.com/item?id=32837565 https://github.com/fumiyas/qrc
* _decode_: 动 convert back to original fmt https://stackoverflow.com/a/31322359
```yaml
1: "A"  # encode
"A": 1  # decode
```
* _character set_: alphabet + syllabary https://en.wikipedia.org/wiki/Character_encoding#Terminology 🗄 `sociology.md` linguistics/grammar
* used synonymously with 'encoding'
> When I discovered that the popular web development tool PHP has almost complete ignorance of character encoding issues, blithely using 8 bits for characters, making it darn near impossible to develop good international web applications, I thought, enough is enough. https://www.joelonsoftware.com/2003/10/08/the-absolute-minimum-every-software-developer-absolutely-positively-must-know-about-unicode-and-character-sets-no-excuses/

🗄 `sociology.md` linguistics
📙
* Bhargava ch. 5
* MacCormick ch. 4

* _format_: rules for information structure https://format.wtf/examples https://en.wikipedia.org/wiki/Format
* _encoding_: rules for conversion from one fmt to another https://en.wikipedia.org/wiki/Code
* used as both noun and verb
* _serialization_: encoding for obj in-mem to text/binary and vice versa https://www.fluentpython.com/lingo/#serialization 📙 Kleppmann [113]
* _protocol_: rules for communication system https://en.wikipedia.org/wiki/Communication_protocol
* sometimes used synonymously with "encoding" https://blainsmith.com/articles/plain-text-protocols/

* _codec_: https://www.fluentpython.com/lingo/#codec https://en.wikipedia.org/wiki/Code

semantics https://stackoverflow.com/a/41217889
* _protocol_: encoding for computer networking https://blainsmith.com/articles/plain-text-protocols/
* impl can interact; e.g. HTTP - JS client can talk to Python server
* overlap with linguistics https://www.unicode.org/versions/Unicode14.0.0/appE.pdf
* representing integers, Google had to switch from 32-bit to 64-bit for Gangnam Style https://www.interviewcake.com/article/python3/data-structures-coding-interview#fixed-width-nums https://danielmiessler.com/study/encoding/ https://kunststube.net/encoding/ https://kunststube.net/frontback/ https://www.joelonsoftware.com/2003/10/08/the-absolute-minimum-every-software-developer-absolutely-positively-must-know-about-unicode-and-character-sets-no-excuses/
* _base64_: 🗄 `4-application.md` 'headers' https://developer.mozilla.org/en-US/docs/Web/HTTP/Authentication#Authentication_schemes

semantics
* _protocol_: fmt https://blainsmith.com/articles/plain-text-protocols/
* "implement protocol/spec" = create library for language to read/write data in that protocol https://msgpack.org/ https://github.com/polyglotted/msgpack-python/tree/master/msgpack https://github.com/aviramha/ormsgpack https://bsonspec.org/faq.html https://bsonspec.org/spec.html
* _serialization_: convert obj to protocol for network transmission 
* _encoding_: protocol to represent non-digital (text, audio) as digital 📙 Petzold ch. 20
* i.e. binary files don't have encoding themselves but have text fields w/ encoding https://stackoverflow.com/a/38264655
* synonym for conversion in general e.g. Morse code dot/dash to electrical signal 📙 Sweigart ciphers 3 https://www.reddit.com/r/AskProgramming/comments/c8pssr/comment/esom0gi/

semantics
* _serialization_: encoding for data interchange 📙 Kleppmann [115] https://www.fluentpython.com/lingo/#serialization
* no one uses language-specific versions e.g. Pickle 📙 Kleppmann [114]

* _encoding_: spec for conversion https://en.wikipedia.org/wiki/Code
* e.g. mp3 spec for how to encode audio 📙 Sweigart 1.3

## ascii

🗄️ `info.md` diagrams

---

* _ASCII_: mapping from number to glyph (char) 📍 Petzold 15.181, computerphile 📚 Petzold code ch. 20 https://www.youtube.com/watch?v=XaGXPObx2Gs from pre 8-bit era; `man ascii` https://increment.com/programming-languages/unplain-text-primer-on-non-latin/

## Unicode

📜 https://www.unicode.org/main.html

```sh
file -i $FILE  # make sure confirms to Unicode
```

---

https://taskwarrior.org/docs/unicode/
https://sw.kovidgoyal.net/kitty/faq/#some-special-symbols-are-rendered-small-truncated-in-kitty
https://crates.io/crates/ucd-trie
https://docs.python.org/2/howto/unicode.html
https://docs.python.org/3/howto/unicode.html
https://mcilloni.ovh/2023/07/23/unicode-is-hard/
https://lucumr.pocoo.org/2014/1/5/unicode-in-2-and-3/
https://codepoints.net/
https://www.pythonmorsels.com/cli-tools/#quopri
https://pyatl.dev/2024/09/01/bitten-by-unicode/
https://text.makeup/about/
https://github.com/AncientNLP/potnia
📍 utf-8 vs. unicode https://youtu.be/SM9gJv08dm0 2:30 https://stackoverflow.com/questions/643694/what-is-the-difference-between-utf-8-and-unicode https://nbviewer.org/gist/guocheng/1ae6c2d76461a66cfc5ec6009b5791d1 https://docs.python.org/3/howto/unicode.html
* emoji, kanji https://www.fluentpython.com/extra/multi-character-emojis/ https://www.textualize.io/blog/posts/7-things-about-terminals how emojis make it into the standard https://www.unicode.org/emoji/proposals.html#frequency-evidence https://news.ycombinator.com/item?id=41844624

* _UTF8_: multi-byte i.e. characters outside of English just get more bytes thrown at them https://sethmlarson.dev/blog/utf-8 https://news.ycombinator.com/item?id=30259097 https://viralinstruction.com/posts/utf8/
* _Unicode_: char set https://stackoverflow.com/a/13212528/6813490 https://github.com/arp242/uni https://www.youtube.com/watch?v=MijmeoH9LT4 https://rentafounder.com/how-to-count-unicode-string-characters/ https://www.dampfkraft.com/ghost-characters.html code point, glyph, octal, hex https://realpython.com/courses/python-unicode/ `unicode-standard.pdf` https://www.joelonsoftware.com/2003/10/08/the-absolute-minimum-every-software-developer-absolutely-positively-must-know-about-unicode-and-character-sets-no-excuses/ https://en.wikipedia.org/wiki/Code_point CLI tool https://github.com/arp242/uni/ in Python https://blog.phylum.io/malicious-actors-use-unicode-support-in-python-to-evade-detection https://news.ycombinator.com/item?id=37735801 https://realpython.com/python-sort-unicode-strings/
* unicode, emoji in the terminal https://news.ycombinator.com/item?id=37047785
> Since the distinction between string and unicode has been done away with in Python 3, __unicode__ is gone and __bytes__ (which behaves similarly to __str__ and __unicode__ in 2.7) exists for a new built-in for constructing byte arrays. https://rszalski.github.io/magicmethods/#appendix2
* Hangul https://news.ycombinator.com/item?id=42228903

## prefix codes

https://gist.github.com/joepie91/26579e2f73ad903144dd5d75e2f03d83 https://en.wikipedia.org/wiki/Prefix_code
* _Huffman coding_: algo used to generate prefix code https://news.ycombinator.com/item?id=22474850 https://en.wikipedia.org/wiki/Huffman_coding
* _prefix code_: encoding mechanism
```yaml
161133
```
* _codeword_: individual values
* cannot share prefix e.g. `[3, 11, 22]` valid but `[1, 11, 22]` invalid bc `1` and `11` share prefix
* decode prefix code by applying codewords
```yaml
# prefix
161133
# codewords
[1, 2, 33, 50, 61]

# must be 1 bc no other codeword can start w/ 1
1 61133
# and so on for rest
1 61 1 33
```

# 🧮 NUMBERS

📚
* Evans ints float
* Evans za

---

📚
* Bryant computer systems ch. 2
* Petzold annotated turing
* Petzold code ch. 7-9
* Shibuya microprocessors ch. 1

SEMANTICS
* _number_: idea used for proofs https://en.wikipedia.org/wiki/Number
* _numeral system_: math notation for representing numbers
* more symbols = less space e.g. hex requires less places than binary
* _radix (base)_: number of digits in number system 📙 Petzold code 186
* fewer number of states = less ambiguity i.e. we don't use ternary or quinary for transistor 📙 Kozeriok 4.63 https://www.youtube.com/watch?v=gI-qXk7XojA 1:20
* _digit_: symbol to represent a number https://en.wikipedia.org/wiki/Numerical_digit

| SYSTEM      | RADIX         | REPR OF 231 | USE [PETZOLD CODE 181]
| ----------- | ------------- | ----------- | ---------------------------------------- |
| binary      | two (0-1)     | 1110111     | precise                                  |
| decimal     | ten (0-9)     | 231         | readable                                 |
| hexademical | sixteen (0-f) | e7          | easy converion to binary (unlike decimal)|
| ----------- | ------------- | ----------- | -----------------------------------------|

## binary

🛠️ https://github.com/jarun/bcal
📚
* Petzold code 3, 9, 12-13
* Evans ints floats

SCALE 📙 Kozierok 4.63
* _bit_: binary digit; aka 'flag' [Kozierok 4.63]
* _byte_: 8 bits
* aka octet, octet string = sequence of bytes https://stackoverflow.com/a/21463473 https://stackoverflow.com/a/1241234
* 255 possible values https://www.youtube.com/watch?v=dPxCGlW9lfM 5:10
* _kilobyte (KB)_: 1k bytes
* _megabyte (MB)_: 
* _gigabyte (GB)_: 1024^3 bytes
* _terabyte (TB)_: 
* _petabyte_: 1024 TB?
* _exabyte_: 1B GB

---

* _bitmask_: toggling bit https://www.arp242.net/bitmask.html set (to 1) reset/clear (to 0) [Kozierok 4.63]
* _nybble_: 4 bits [Petzold code 181]
* _byte string_: sequence of bytes https://stackoverflow.com/a/31322359 https://www.fluentpython.com/lingo/#byte_string
* _bit width_: number of bits needed to represent an int e.g. on Intel processors ints are 4 bytes wide https://boredzo.org/pointers/#starting
* add by carrying over e.g. 1 + 1 = 10 [Manga 1.43]
* _two's complement_: how to do substraction on binary, represent negative numbers [Petzold code 15.180, Petzold code 12-13 Manga 1.44-46]
* _high-order bit (MSB)_: bit position w/ greatest value e.g. in 101 the eighths position is the MSB https://en.wikipedia.org/wiki/Bit_numbering also used to mean "most salient point"  https://danluu.com/corp-eng-blogs/ https://diff.substack.com/p/big-tech-sees-like-a-state

decimal in binary
* _unsigned_: positive
* _signed_: positive and negative; can reserve leftmost bit for sign https://www.interviewcake.com/article/python3/data-structures-coding-interview#binary-numbers
* _fixed width_: has specific size e.g. 32 or 64 bits https://www.interviewcake.com/article/python3/data-structures-coding-interview#fixed-width-nums
* _floating point_: 1,230,000 as 1.23 (significand) * 10^6 (exponent) w/ significand as always greater than 1 but less than 2 [manga 42-3]; faster for CPU computation; makes getting a high-level language to behave like your desktop calculator more difficult than you'd expect https://stefanoborini.com/why-01-plus-02-is-not-03-in-python/ https://docs.python.org/3/tutorial/floatingpoint.html https://stackoverflow.com/a/46700365/6813490 https://stackoverflow.com/a/50340297/6813490 https://0.30000000000000004.com/ fractions also get weird, too https://orbifold.xyz/numbers.html 📜 Van Rossum ch. 8 https://jvns.ca/blog/2023/01/13/examples-of-floating-point-problems/ https://jvns.ca/blog/2023/01/13/examples-of-floating-point-problems/ https://github.com/francisrstokes/githublog/blob/main/2024%2F5%2F29%2Ffast-inverse-sqrt.md
> 10000 is 100%. We're using integers so that we're not using floats. Floats and money are a bad combination. https://jvns.ca/blog/2023/02/08/why-does-0-1-plus-0-2-equal-0-30000000000000004/
> https://ciechanow.ski/exposing-floating-point/
```python
value = 0.1 + 0.2
f"{val:.{1}}"  # 0.3
val = 45 * (0.1 + 0.2)
f"{val:.{4}}"  # 13.5
```

## hex

📚 Petzold code ch. 15

TOOLING
* _heh_: https://github.com/ndd7xv/he
* _hexowl_: https://github.com/dece2183/hexowl
* _hexyl_: ✅ viewer https://github.com/sharkdp/hexyl 🗄️ uuinfo

---

📍 learn C, learn how to edit binary https://www.youtube.com/watch?v=-eDY7yh-CyA https://danluu.com/edit-binary/

* used bc easier to convert to binary than decimal 📙 Petzold code [181] https://www.youtube.com/watch?v=dPxCGlW9lfM [4:20]
* _hexit_: hex digit (1 nybble) https://www.youtube.com/watch?v=dPxCGlW9lfM [4:30]
* used for reverse engineering? https://github.com/radareorg/radare2

TOOLING
* `hexdump -C <file>` https://www.youtube.com/watch?v=-eDY7yh-CyA [1:50]
* _fq_: query https://github.com/wader/fq 
* _hevi_: https://github.com/Arnau478/hevi
* _hexabyte_: 🎯 editor https://github.com/thetacom/hexabyte
* _hexedit_: Ubuntu https://news.ycombinator.com/item?id=23762626
* _hexed_: 🎯 browser https://hexed.it/
* _HexFiend_: macOS https://github.com/HexFiend/HexFiend
* _ImHex_: 🎯 editor https://github.com/WerWolv/ImHex 

# 🟨 ZA

CASES https://ls-lint.org/blog/announcements/v2.3.0.html#what-the-heck-is-ls-lint https://github.com/zobweyt/textcase
* _snake_: `hello_world`
* _kebab_: `hello-world`
* _camel_: `helloWorld`
* _Pascal_: `HelloWorld`
* _Sponge Bob_: `hElOo wOrLd`
* _Brad_: `hello.world`

## identifiers

🏔️ https://eieio.games/blog/writing-down-every-uuid/

TOOLS
```sh
uuidgen | tr '[:upper:]' '[:lower:]' | pbcopy  #  https://weiyen.net/articles/useful-macos-cmd-line-utilities
python -c "import random, string; print('\n'.join(''.join(random.choices(string.ascii_uppercase + string.digits, k=4)) for _ in range(20)))"
```
* _uuinfo_: ✅ identify UUID, Snowflake IDs https://github.com/Racum/uuinfo 🗄️ hexyl
* _pwgen_: generate https://www.youtube.com/watch?v=G3aH2WYJxGA
* _shortuuid_: https://github.com/skorokithakis/shortuuid https://github.com/lithammer/shortuuid

TYPES
* _QR code_: generate https://calmcode.io/course/qr-code/generate
* _DUNS_: unique for businesses as legal entities e.g. `00-186-7803` (Apple)
* required for SSL certs, government contracts, to be a supplier to big businesses
* _ASIN_: Amazon SKU e.g. `B0CGJVLF9Q` (Pink Floyd dark side of the moon)
* per product i.e. if multiple sellers sell same product they use same ASIN https://inventlikeanowner.com/blog/the-story-behind-asins-amazon-standard-identification-numbers/
```python
import random
import string
'B' + ''.join(random.choices(string.ascii_uppercase + string.digits, k=9))
```
* _SKU_: internal ID; variable length, fmt repr product characteristics/location
* _UPC_: external ID i.e. unique across retailers
* GS1 oversees UPCs + GLN (global location) NSN (national stock) EAN (European article) SSCC (shipping containers) GTIN (UPC superset) https://www.gs1.org/
```sh
# syntax: manufacturer + product + check digit (proof of correct reading of previous digits)
049000000156  # coke classic 12 oz can
049000000163  # coke diet 12 oz can
049000000187  # sprite 12 oz can
```
```python
def calculate_check_digit(upc_without_check_digit):
    """
    calculate check digit for given UPC w/ Modulo 10 algo
    args: upc_without_check_digit (str): first 11 digits of the UPC w/o the check digit
    returns: int: calculated check digit
    """
    # convert input string to list of ints
    digits = [int(d) for d in upc_without_check_digit]
    # multiply odd-positioned digits (0-indexed) by 3 and even-positioned digits by 1
    total = 0
    for i, digit in enumerate(digits):
        if i % 2 == 0:  # Odd positions in 0-indexed (1, 3, 5...)
            total += digit * 3
        else:  # Even positions in 0-indexed (2, 4, 6...)
            total += digit
    # calc check digit
    remainder = total % 10
    check_digit = (10 - remainder) if remainder != 0 else 0
    return check_digit

# diet coke 12 oz can
upc_input_diet_coke = "049000028911"
# extract first 11 digits (excluding the check digit)
upc_without_check_digit_diet_coke = upc_input_diet_coke[:11]
# calc check digit for the provided UPC
calculated_check_digit_diet_coke = calculate_check_digit(upc_without_check_digit_diet_coke)
# construct full UPC with the calculated check digit
full_upc_diet_coke = upc_without_check_digit_diet_coke + str(calculated_check_digit_diet_coke)
# output
print(f"UPC without check digit: {upc_without_check_digit_diet_coke}")
print(f"Calculated check digit: {calculated_check_digit_diet_coke}")
print(f"Full UPC: {full_upc_diet_coke}")
```

---

McMaster Carr
* https://www.mcmaster.com/92949A050/
> If you're familiar with McMaster, you might recognize how their number is semi-smart: the first section (91257) is the general product while the second section (546) is a variant within that.
> This is a "semi-smart" numbering system - not completely arbitrary but not fully semantic either. It balances: Categorization (first segment) Variation tracking (last segment) Human readability (letter break)

UUID https://www.rfc-editor.org/rfc/rfc9562.html https://www.ntietz.com/blog/til-uses-for-the-different-uuid-versions/ https://en.wikipedia.org/wiki/Universally_unique_identifier https://taskwarrior.org/docs/dom/
* prefixed https://github.com/minhajuddin/prefixed_uuids
* version 1: generated from timestamp, monotonic counter, and a MAC address
> don't use
* version 2: reserved for security IDs with no known details
* version 3: generated from MD5 hashes of some data you provide; RFC suggests DNS and URLs among the candidates for data.
> superseded by version 5
* version 4: generated from entirely random data; this is probably what most people think of and run into with UUIDs.
> default
* version 5: generated from SHA1 hahes of some data you proivde; RFC suggests DNS or URLs as candidates for data.
> if you have your own data you want in the UUID
* version 6: generated from timestamp, monotonic counter, and a MAC address; same data as Version 1 but they change the order so that sorting them will sort by creation time.
> don't use
* version 7: generated from a timestamp and random data.
> if you're using in a context where you want to be able to sort e.g. database keys
* version 8: entirely custom (besides the required version/variant fields that all versions contain).
> if you have your own data you want in the UUID

## standards bodies

🗄️ EDI > meta

ANSI (American National Standards Institute)
* SQL
* used to do C 📙 Beaulieu [5.86]
* escape codes https://notes.burke.libbey.me/ansi-escape-codes/

ISO (International Standards Org)
* does C now, C++ https://www.iso.org/standard/68564.html
* created OSI
* credit cards https://www.iso.org/standard/79451.html https://news.ycombinator.com/item?id=42442354

---

* how RFCs work https://stackoverflow.com/a/1961018
> There are standards track documents and non-standard track (informational) documents. The entire process, including descriptions, processes and rules for IETF issued documents is defined by RFC2026 with some follow on amendments. Every RFC will specify at the beginning which track it is on. https://datatracker.ietf.org/doc/html/rfc2026
> RFC is an acronym that stands for "Request For Comments," meaning it is intended on gathering feedback from the community. That being said, almost the entire internet runs on unratified RFCs, or less. The CSV "standard" itself is essentially undefined without RFC4180. It is the most definitive model we have although it might change someday. As it stands, RFC4180 has no provisions for inserting comments. If you add your own commenting mechanism to the format, don't expect interoperability with other reader/writers that follow RFC4180. https://datatracker.ietf.org/doc/html/rfc4180
* "technical committees, international standards organizations, and government agencies that manage the Internet" - Network Know-How [36]
* why USSR didn't invent the internet http://web.mit.edu/slava/homepage/articles/Gerovitch-InterNyet.pdf
* _sink_: https://en.wikipedia.org/wiki/Internet_Society RFCs https://tangentsoft.net/rfcs/by-tla.html
* _IETF_: HTTP https://tools.ietf.org/html/rfc7617
* _IEEE (Institute for Electrical Electronic Engineers)_: POSIX (standard for UNIX-like OS, C, Bash) [LPI 1.3.2] https://ieeexplore.ieee.org/document/6359709 https://en.wikipedia.org/wiki/Institute_of_Electrical_and_Electronics_Engineers
* _Open Group_: controls UNIX (which is just a spec; Solaris, macOS); IBM Huawei DoD Nasa that controls; no Linux distro qualifies [LPI 1, 1.3.3]
* https://diff.substack.com/p/sharing-and-owning-standards
* [Cloud Native Computing Foundation](https://changelog.com/podcast/314)
* [how to read an RFC](https://www.mnot.net/blog/2018/07/31/read_rfc)
* https://wiki.creativecommons.org/wiki/Case_Studies/StackOverflow.com
* http://www.ieee802.org/3/ --> people that do work for the IEEE work for semiconductor companies
* http://yehudakatz.com/about/
* http://yehudakatz.com/podcasts/
* https://softwareengineeringdaily.com/host/
* https://blogs.windows.com/msedgedev/2017/10/18/documenting-web-together-mdn-web-docs/
* Linux Programming Interface: chapter 1

## structure

* _unstructured text_: e.g. Unix tools
* flexible http://www.catb.org/~esr/writings/taoup/html/ch05s01.html https://news.ycombinator.com/item?id=23630640
* leads to complexity https://danluu.com/cli-complexity/ 
* _structured text_: e.g. Powershell, JSON, CSV, XML, HTTP/1 https://news.ycombinator.com/item?id=27431998
* operating systems use of https://news.ycombinator.com/item?id=28301646
